# slack-exporter

A Slack bot and standalone script for exporting messages and file attachments from public and private channels, using Slack's new Conversations API.

A similar service is provided by Slack for workspace admins at [https://my.slack.com/services/export](https://my.slack.com/services/export) (where `my` can be replaced with your full workspace name to refer to a workspace different than your default). However, it can only access public channels, while `slack-exporter` can retrieve data from any channel accessible to your user account.

## Authentication with Slack

1. Visit [https://api.slack.com/apps/](https://api.slack.com/apps/) and sign in to your workspace.
2. Click `Create New App`, enter a name (e.g., `Slack Exporter`), and select your workspace.
3. In prior versions of the Slack API, OAuth permissions had to be specified manually. Now, when prompted for an App Manifest, just paste in the contents of the `slack.yaml` file in the root of this repo.
4. Select `Install to Workspace` at the top of that page (or `Reinstall to Workspace` if you have done this previously) and accept at the prompt.
5. Copy the `OAuth Access Token` (which will generally start with `xoxp` for user-level permissions)

## Usage

`exporter.py` can create an archive of all conversation history in your workspace which is accessible to your user account.

1. Either add 

    ```text
    SLACK_USER_TOKEN = xoxp-xxxxxxxxxxxxx...
    ```
    
    to a file named `.env` in the same directory as `exporter.py`, or run the following in your shell (replacing the value with the user token you obtained in the [Authentication with Slack](#authentication-with-slack) section above).

    ```shell script
    export SLACK_USER_TOKEN=xoxp-xxxxxxxxxxxxx...
    ```

2. Run `python exporter.py --help` to view the available export options.

## License

This software is available under the [GPL](LICENSE).

Inspired by [slack-exporter](https://github.com/sebseager/slack-exporter)