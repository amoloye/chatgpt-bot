# chatgpt-bot API

# Registration and Api Integration
1. Register and Sign-in into "OpenAI" platform.
2. Vist "https://platform.openai.com/playground".
3. Under "User", type in your query just like using chatgpt itself.
4. click on "View code" to check the "request" to be made in "curl" format. If not in "Curl" format click the drop-down on the "POST /v1/chat/completions" page and change it to "curl"
5. Visit your "Postman" and "import" this code as "rawtext".
6. click the body to get this code in Json Format.

# Authorization and Bearer Token
1. Goto "https://platform.openai.com/account/api-keys" and "Create new Secret key".
2. Copy the key, and put the key in Postman-> Authorization-> Type -> Bearer Token.
3. paste this key in the Token box.
4. change your postman HTTp request to post and use this url "https://api.openai.com/v1/chat/completions" or the url on top of the page when you clicked view code on the page "https://platform.openai.com/playground".
5. Send your Request on postman to get a Response.

# API
1. Create a Model/DTO/Entity using the Request and Response as indicated on the Postman, also, create the "Message" and "Choice" class all in the "Model/DTO/Entity" layer .
2. Create the Config package, and configure the rest Template to contain the OpenaiApiKey, as the key is also parsed in the application.properties file.
3. Since it is a small microservice, service layer might not be needed, but in the controller layer, call the RestTemplate class from the config package and make a new Request in the "chat" method.
4. Note that when parsing the String "prompt" which is also the content as in the Message dto, the role is always "user" when it concerns making a request.
5. The response should look like this "= template.postForObject(apiURL, request,ChatGptResponse.class)" using the RestTemplate and return only the content as in "chatGptResponse.getChoices().get(0).getMessage().getContent()"

# Dependencies
1. Lombok
2. Spring Web
