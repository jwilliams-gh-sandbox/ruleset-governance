# :construction_worker: This is a WIP

### Steps to find UI settings from [github.com](https://github.com/):
<table width="100%">
    <thead>
        <tr>
            <th>Entity</th>
            <th>Steps</th>
            <th>Link</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Enterprise</td>
            <td>
                1. Select your profile image from the header.<br />
                2. Select <i>Enterprises</i>.<br />
                3. Select the appropriate enterprise.<br />
                4. Select <i>Policies</i>.<br />
                5. Select <i>Repository</i> -> <i>Repository</i>.
            </td>
            <td>https://github.com/enterprises/<var>&lt;ENTERPRISE SLUG&gt;</var></td>
        </tr>
        <tr>
            <td>Organization</td>
            <td>
                1. Select your profile image from the header.<br />
                2. Select <i>Organizations</i>.<br />
                3. Select the appropriate organization.<br />
                4. Select <i>Settings</i>.<br />
                5. Select <i>Repository</i> -> <i>Rulesets</i> -> <i>New ruleset</i> || <i>Select &lt;RULESET NAME&gt;</i>.
            </td>
            <td>https://github.com/<var>&lt;ORGANIZATION SLUG&gt;</var></td>
        </tr>
        <tr>
            <td>Repository</td>
            <td>
                1. Select your profile image from the header.<br />
                2. Select <i>Repositories</i> OR Select the appropriate organization -> <i>Repositories</i>.<br />
                3. Select the appropriate repository.<br />
                4. Select <i>Settings</i>.<br />
                5. Select <i>Rules</i> -> <i>Rulesets</i> -> <i>New ruleset</i> || <i>Select &lt;RULESET NAME&gt;</i>.
            </td>
            <td>https://github.com/<var>&lt;ORGANIZATION SLUG&gt;</var>/<var>&lt;REPO NAME&gt;</var></td>
        </tr>
    </tbody>
</table>


```mermaid
---
title: High Level POC Plan - v0
---
flowchart LR
    subgraph optional_ui["OPTIONAL - GitHub UI"]
        direction TB
        choose_playground["Choose a safe playground org"] --> follow_steps["Follow the #quot;Organization#quot; steps above to create a new ruleset"]
        follow_steps --> define_props["Define the ruleset"]
        define_props --> create["_Create_/_Save Changes_"]
        create --> select_ruleset["Select ruleset"]
        select_ruleset --> export["From the _..._ additional options, select _Export ruleset_"]
        export --> download["Open the downloaded _&lt;RULESET NAME&gt;.json_ file"]
    end

    subgraph edit_rulesets["Edit Ruleset Files<br />Note: The instructions below use the git cli."]
        direction TB
        pick_ide["Pick an IDE"] --> cd_repo["`cd &lt;PATH TO DEDICATED RULSET GOVERNANCE REPO&gt;`"]
        cd_repo --> git_pull["`git pull`"]
        git_pull --> git_checkout["`git checkout -b &lt;BRANCH-NAME&gt;`"]
        git_checkout --> edit_file["Edit the ruleset json file"]
        edit_file --> gcam["`git add &lt;EDITED FILE PATH&gt; && git commit -m #quot;&lt;COMMIT MESSAGE&gt;#quot;`"]
        gcam --> git_push["`git push -u origin head`"]
        git_push --> create_pr["Create PR"]
        create_pr --> push_default["Push to the _default_ branch"]
    end

    optional_ui optional_ui_to_edit_rulesets@--> edit_rulesets

    subgraph automation["Automation"]
        direction TB
        workflow_trigger["A workflow is triggered on the push to the _default_ branch"] --> workflow_diff_discovery["Upsert made to ruleset"]
    end

    edit_rulesets edit_rulesets_to_automation@--> automation

    classDef animate_arrow stroke: #555, stroke-linecap:round, stroke-dasharray: 1 10 5 10, stroke-dashoffset: 500px, stroke-width:3px, animation: dash 50s linear infinite;

    class optional_ui_to_edit_rulesets animate_arrow
    class edit_rulesets_to_automation animate_arrow
```