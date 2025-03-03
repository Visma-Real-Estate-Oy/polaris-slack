# polaris-slack
Slack integration for Synopsys Coverity on Polaris

The functionality of this script is to alert on new issues in any Polaris project that a service account has access to.

But you are in charge of running this script after your normal Polaris snapshot process.

You can configure which issues (eg only security or untriaged) are being reported.

## Required Environment Variables

|VariableName|Type|Example|
|---|---|---|
|POLARIS_URL|Uri|`http://example.polaris.synopsys.com/`|
|POLARIS_TOKEN|string|`examplepolaritoken`|
|SLACK_WEBHOOK_URL|Uri|`https://hooks.slack.com/services/XXXX/YYYY/zzzzz`|
|SLACK_ONE_MESSAGE_PER_PROJECT|Boolean|true (optional)|
|POLARIS_FILTER_ONLY_SECURITY|Boolean|true (optional)|
|POLARIS_FILTER_ONLY_UNTRIAGED|Boolean|true (optional)|
|POLARIS_FILTER_ONLY_MED_HIGH|Boolean|true (optional)|

## Optional Environment Variables explained

- SLACK_ONE_MESSAGE_PER_PROJECT
    - boolean to send one message per project so you can easily start thread per project in slack.
- POLARIS_FILTER_ONLY_MED_HIGH
    -  boolean to filter only medium and high issues.

## Usage with docker

```bash
docker build -t polaris-slack:example
docker run -e POLARIS_URL -e POLARIS_TOKEN -e SLACK_WEBHOOK_URL polaris-slack:example
```

## Usage from cli

### Bash
```bash
python3 -m venv venv
source venv/Scripts/activate
python3 -m pip install -r requirements.txt
python3 main.py
```

### Powershell
```powershell
python3 -m venv venv
./venv/Scripts/Activate.ps1
python3 -m pip install -r requirements.txt
python3 main.py
```

## Example Output

![Example Output](/example.png?raw=true "Example Output")
