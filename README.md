Build An Alexa Quiz Skill in Python using ASK Python SDK
=============

![Tutorial Header](https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/fact/header._TTH_.png)

[![Voice User Interface](https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/navigation/1-on._TTH_.png)](./instructions/1-voice-user-interface.md)[![Lambda Function](https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/navigation/2-off._TTH_.png)](./instructions/2-lambda-function.md)[![Connect VUI to Code](https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/navigation/3-off._TTH_.png)](./instructions/3-connect-vui-to-code.md)[![Testing](https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/navigation/4-off._TTH_.png)](./instructions/4-testing.md)[![Customization](https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/navigation/5-off._TTH_.png)](./instructions/5-customization.md)[![Publication](https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/navigation/6-off._TTH_.png)](./instructions/6-publication.md)

## What You Will Learn
*  [AWS Lambda](http://aws.amazon.com/lambda)
*  [Alexa Skills Kit (ASK)](https://developer.amazon.com/alexa-skills-kit)
*  Using the [Skill builder (beta)](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/ask-define-the-vui-with-gui)
*  Voice User Interface (VUI) Design

## What You Will Need
*  [Amazon Developer Portal Account](http://developer.amazon.com)
*  [Amazon Web Services Account](http://aws.amazon.com/)
*  The sample code on [GitHub](https://github.com/dixonaws/autoguide).
*  [ASK Python SDK](https://github.com/alexa/alexa-skills-kit-sdk-for-python)
*  A basic understanding of Python.

## Instructions
1. Use the ASK CLI to create a new Alexa skill based on this repository
ask new --template --skill-name "autoguide" --url https://www.dixonaws.com/alexaskills.json
 
2. Install the dependencies in the lambda/py directory
Enter the repo directory, e.g. ```autoguide/lambda/py```
Install dependencies from requirements.txt with ```pip install -r requirements.txt -t .```
This will install all of the dependencies that the Lambda function will need to execute 
when invoked by the Alexa skill 


3. Update the Lambda function
/// to use Python and an environment variable for the TripTable
// Add an IAM role that can access your VehicleTripTable
// Edit lambda-update-function-configuration.json to do this in one step

// get the lambda skill name
// need jq
cat .ask/config | jq .deploy_settings.d

```bash
aws lambda update-function-configuration --cli-input-json fileb://lambda-update-function-configuration.json
```

need to also include json for IAM role which can access the dynamoTripTable

4. Deploy the skill
Run ```ask deploy``` from the directory


## What Your Skill Will Do
The Skill allows users to request a quiz about the 50 States of the USA. They will receive 10 random questions or they can ask for specific information, such as, "tell me about New York".
This simple "quiz" skill will teach you how the different pieces of the Alexa Skill development process fit together.

We use will use the Skill builder UI to build the Skill although the quiz itself does not employ the new "Dialog-Delegate interface" model.

