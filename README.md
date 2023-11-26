# GPT/Whisper/DALL-E Telegram Bot with easy deployment using Chalice to AWS Lambda
<p align="left">
<img
  src="https://user-images.githubusercontent.com/1978717/227817754-219a8e0d-8a79-4cbb-8d1e-e348887bfa73.jpg"
  alt="Bot Demo"
  title="Happy Programmer"
  style="display: inline-block; margin: 0 auto; max-width: 150px; width: 324px; height: 657px">
</p>

GPT/Whisper/DALL-E Telegram Bot using AWS features

- Lambda, DynamoDB (full auto-deployment)
- ~~Fargate, ECS (manual Docker container deployment)~~ Deprecated

## Requirements

- Python 3.9+
- AWS CLI
- AWS credentials and region setup in the \`~/.aws/credentials\` file
- Chalice

## Deployment to AWS Lambda

1. Create a Free Tier AWS account

2. Install and setup AWS CLI (region must be specified in ~/.aws/credentials. Ex.: region=eu-west-1)

3. Update the \`.chalice/config.json\` file with your Telegram Bot API, OpenAI API Token, and your telegram userID (get it from @userinfobot).

4. Run the `deploy.sh` script to deploy the Telegram Bot to AWS Lambda (or `deploy.sh name` for a custom config)

For voice processing you will need to do the next manually (it will be automated in the next releases):

1. Upload ffmpeg.zip to your S3 bucket
2. Create Lambda Layer using S3 URI
3. Attach layer to your Lambda function

## Features

- Currently used openAI model: gpt-3.5, gpt-4 (Choose in config or by the bot's command)
- Image generation `/image prompt` or just ask without the command!
- Voice message transcript (Just send any voice message)
- Video transcript and translation! (Send any video to the bot, and it will transcribe and translate it to English)
- The context of your chat is saved until you use the command `/clear`
- The price in USD of the response is shown
- Multi-config support: keep multiple chalice configs to deploy multiple bots `.chalice/name.config.json`
