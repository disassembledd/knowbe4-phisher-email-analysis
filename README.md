# KnowBe4 PhishER Email Analysis
This is an agent-empowered n8n workflow that will pull outstanding reported emails in the PhishER platform for analysis, provide its overview, and then submit a tag and comment to the message within the platform.
> This agent requires minor additions to an n8n deployment in order to function, and assumes the use of AWS Bedrock. This README is not intended to be a guide on how to deploy a production n8n instance either, as their docs will be kept up to date with the best standards on doing so. You can also copy the prompt itself from `prompt.txt` if you just want that to use in your own platform/script.

----

## How to use this
In order to import this into your n8n instance and it work, you will need to create a `Dockerbuild` file that installs `mailparser`, `htmlparser2`, `domutils`, and `dom-serializer` for your runners or main instance if you aren't using runners. Those are used in the code node `Parse Raw URL for Email Content` which, among other things, is responsible for scraping the embedded images that may have been present in a reported email. You will also need to add the credentials for the following nodes: `Retrieve all PhishER Messages from today`, `Add Analysis to PhishER Message`, `Add Tag to PhishER Message`, and `Prompt Model`.

If you will be using n8n, within the `Prompt Model` node will be the prompt itself. You should update the following:
- Under `4. **ANALYZE LINKS AND DOMAINS:**`, the safe link for Outlook is default (`safelinks.protection.outlook.com`). You should update this for your corresponding email security platform.
- Under `- **ALLOWLIST:**` will be two placeholder domains (`<whitelisted-domain-X>`) that the AI should generally whitelist instead of considering them potentially malicious for not being your organization's domain.
- Under `### TRUSTED DOMAINS ###` will be Microsoft/Outlook domains by default that are generally trusted sources. These can be replaced and/or updated to other domains your organization wants to have as more trusted.

## Screenshots
