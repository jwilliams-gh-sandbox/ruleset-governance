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
            <td>Enterprise</td>
        </tr>
        <tr>
            <td>Organization</td>
            <td>
                1. Select your profile image from the header.<br />
                2. Select <i>Organizations</i>.<br />
                3. Select the appropriate organization.<br />
                4. Select <i>Settings</i>.<br />
                5. Select <i>Repository</i> -> <i>Rulesets</i> -> <i>New ruleset</i>.
            </td>
            <td>Organization</td>
        </tr>
        <tr>
            <td>Repository</td>
            <td>
                1. Select your profile image from the header.<br />
                2. Select <i>Repositories</i> OR Select the appropriate organization -> <i>Repositories</i>.<br />
                3. Select the appropriate repository.<br />
                4. Select <i>Settings</i>.<br />
                5. Select <i>Rules</i> -> <i>Rulesets</i> -> <i>New ruleset</i>.
            </td>
            <td>Repository</td>
        </tr>
    </tbody>
</table>


```mermaid
---
title: High Level POC Plan (alpha)
---
flowchart TB
    subgraph "GitHub UI"
    select_repo@{ shape: rect, label: "Select Repository"} --> ...
    end
```