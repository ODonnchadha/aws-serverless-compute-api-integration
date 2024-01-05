## Serverless Compute and API Integration Approaches on AWS

- SERVERLESS COMPUTE:
    - Serverless compute services:
        - AWS Lambda: 
            1. Billed upon useage. Requests and provisioned resources.
            2. Provides prebuilt runtimes for common playforms. (Know tyour version.)
            3. Rwquires new tools for local development and deployment.
            4. Primary service for integration with other event-driven AWS services.
            5. Works seamlessly with API Gateway.
        - AWS Fargate:
            1. Billed based upon duration. Resources deployed for an amount of time.
            2. Utilizes a container that you maintain. As opposed to runtimes.
            3. Does not require cluster configuration.
            4. Enables a more traditional development flow with Docker.
            5. Can be run on either ECS or EKS.
            6. Works seamlessly with API Gateway.
        - To achieve the goals of serverless, use AWS Lambda whenever possible.
    - AWS Lambda Deep Dive:
        - Launching a Lambda function:
            - Define the resources available. 
                - (1) Timeoout value. From three seconds to fifteen minutes. 
                - (2) Allocate memory. 128 to 10,240 MB. (& CPU Power.)
            - Define runtime and associated layers.
                - Add in a runtime in order to run custom code. Many are provided.
                - AWS provides layers. Have things that are installed.
                    - Providing additional native or platform libraries.
                    - Sharing common code between functions.
                    - Implementing a custom runtime.
            - Define permissions.
                - An execution role defined which enables IAM role utilization for access control and permissions to other AWS services.
            - And define, or configure, the environment.
                - Environment variabvles available at runtime,
            - And use the custom code.
                - You *can* utilize a code editor to modify.
        - Key compute differences:
            - Disposable compute. You cannot assume the function will be around.
            - Cold starts. Anytime Lambda has to spin up, there's an initial cost.
            - Concurrency. Multiple functions at a given time to meet demands. Account for this.
    - Working with AWS Lambda:
        - Demo: Create a new Lambda within console. Then modify configuration. Deploy changes to function code and integrate with DynamoDb.

- AWS STEP FUNCTIONS:
    - Overview:
        - A workflow.
            1. Check file.
            2. Get Metadata about the file.
            3. Get thumbnail and extract text.
            4. Insert into database.
            - Alert the user of failure at *any* step.
        - Step functions: A serverless orchestration service. State machine. Each state has I/O data associated with it.
            - Each state includes a stransition to a different state.
            - Allowing for a combination of AWS Lambda functions and other AWS Services to build business-critical applications.
            - Standard workflows:
                1. Can last up to one year.
                2. Proces by state transition.
                3. Asynchronous execution.
                4. Workflows are executed exactly only once.
            - Express workflows:
                1. Can last up to five minutes.
                2. Priced per execution including duration and memory consumption.
                3. Async/sync.
                4. Asynchronous: Can be executed at least once. Synchronous: Executed at most once.
                5. Does not support all async integration models.
            - Express workflows can provide significant saving.
            - Step functions are defined using Amazon States Language.
            - There are pre-defined task types:
                1. Task
                2. Pass (Transform data.)
                3. Choice. (Do this with this thing.)
                4. Wait.
                5. Parallel. Map.
                6. Succeed. Fail.
                - Each task can define how its input and output values will be handled.
            - AWS Service integrations:
                - Lambda. Batch. DynamoDB. ECS, Fargate, anbd EKS. SNS and SQS. Glue, EMR, anbd Athena.
                - SageMaker. COdeBuild. API Gateway. Step Functions. (Can call another step function.)
    - Working with Step Functions:
        - Demo: Creating a basic step function. Testing the step function. Deploying and testing an integrated step function.

- AMAZON API GATEWAY:
    - Overview:
        - Common API needs:
            1. Auth. Authentication and authorization.
            2. Caching.
            3. Disparate sources.
            4. Audit trail.
            5. Throttling.
            6. Application firewall.
        - An AWS service for creating, publishing, maintaining, monitoring, and securing REST, HTTP, and Websocket APIs at any scale.
        - These APIs can access AWS or other Web services, as well as cloud-stored data.
        - API types:
            - REST API:
                1. Useage plans and API keys.
                2. API caching.
                3. Request body transformation
                4. Request and response validation.
                5. Canary release deployment.
                6. Supports Web application firewall.
                7. $3.50 for the first one million calls.
            - HTTP API:
                1. Supports OpenID COnnect/OAuth 2.0
                2. Supports default stage and route configuration.
                3. Supports private ALB and Cloud Map.
                4. $1.00 for the first one million calls.
            - For serverless applications, use HTTP API unless you have specific need(s) you can't meet using it.
            - Websocket API:
    - Working with API Gateway:
        - Demo: Integrating a lambda functioon with API Gateway. And then testing.
    - Cleaning Up:
        - Remove the demo code. Do not incur the associated charges.
    - Next Steps:
        - Via *this* learning path:
        - Building a Serverless API Tier with Amazon API Gateway