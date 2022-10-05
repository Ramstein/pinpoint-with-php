# AWS Pinpoint with PHP

## 1.  Installing the aws SDK for PHP
Installation https://docs.aws.amazon.com/sdk-for-php/v3/developer-guide/getting-started_installation.html

Documentation is available on aws php sdk https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-pinpoint-2016-12-01.html

## 2. Steps to Buildin customer expereinces with amazon pinpoint
### 1. Create a segment in the Application
### CreateSegment 
* Creates a new segment for an application or updates the configuration, dimension, and other settings for an existing segment that's associated with an application.
 ```
$result = $client->createSegment([/* ... */]);
$promise = $client->createSegmentAsync([/* ... */]);
```

Parameter Syntax
```
$result = $client->createSegment([
    'ApplicationId' => '<string>', // REQUIRED
    'WriteSegmentRequest' => [ // REQUIRED
        'Dimensions' => [
            'Attributes' => [
                '<__string>' => [
                    'AttributeType' => 'INCLUSIVE|EXCLUSIVE|CONTAINS|BEFORE|AFTER|BETWEEN|ON',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                // ...
            ],
            'Behavior' => [
                'Recency' => [
                    'Duration' => 'HR_24|DAY_7|DAY_14|DAY_30', // REQUIRED
                    'RecencyType' => 'ACTIVE|INACTIVE', // REQUIRED
                ],
            ],
            'Demographic' => [
                'AppVersion' => [
                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                'Channel' => [
                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                'DeviceType' => [
                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                'Make' => [
                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                'Model' => [
                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                'Platform' => [
                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
            ],
            'Location' => [
                'Country' => [
                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                'GPSPoint' => [
                    'Coordinates' => [ // REQUIRED
                        'Latitude' => <float>, // REQUIRED
                        'Longitude' => <float>, // REQUIRED
                    ],
                    'RangeInKilometers' => <float>,
                ],
            ],
            'Metrics' => [
                '<__string>' => [
                    'ComparisonOperator' => '<string>', // REQUIRED
                    'Value' => <float>, // REQUIRED
                ],
                // ...
            ],
            'UserAttributes' => [
                '<__string>' => [
                    'AttributeType' => 'INCLUSIVE|EXCLUSIVE|CONTAINS|BEFORE|AFTER|BETWEEN|ON',
                    'Values' => ['<string>', ...], // REQUIRED
                ],
                // ...
            ],
        ],
        'Name' => '<string>',
        'SegmentGroups' => [
            'Groups' => [
                [
                    'Dimensions' => [
                        [
                            'Attributes' => [
                                '<__string>' => [
                                    'AttributeType' => 'INCLUSIVE|EXCLUSIVE|CONTAINS|BEFORE|AFTER|BETWEEN|ON',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                // ...
                            ],
                            'Behavior' => [
                                'Recency' => [
                                    'Duration' => 'HR_24|DAY_7|DAY_14|DAY_30', // REQUIRED
                                    'RecencyType' => 'ACTIVE|INACTIVE', // REQUIRED
                                ],
                            ],
                            'Demographic' => [
                                'AppVersion' => [
                                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                'Channel' => [
                                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                'DeviceType' => [
                                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                'Make' => [
                                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                'Model' => [
                                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                'Platform' => [
                                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                            ],
                            'Location' => [
                                'Country' => [
                                    'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                'GPSPoint' => [
                                    'Coordinates' => [ // REQUIRED
                                        'Latitude' => <float>, // REQUIRED
                                        'Longitude' => <float>, // REQUIRED
                                    ],
                                    'RangeInKilometers' => <float>,
                                ],
                            ],
                            'Metrics' => [
                                '<__string>' => [
                                    'ComparisonOperator' => '<string>', // REQUIRED
                                    'Value' => <float>, // REQUIRED
                                ],
                                // ...
                            ],
                            'UserAttributes' => [
                                '<__string>' => [
                                    'AttributeType' => 'INCLUSIVE|EXCLUSIVE|CONTAINS|BEFORE|AFTER|BETWEEN|ON',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                // ...
                            ],
                        ],
                        // ...
                    ],
                    'SourceSegments' => [
                        [
                            'Id' => '<string>', // REQUIRED
                            'Version' => <integer>,
                        ],
                        // ...
                    ],
                    'SourceType' => 'ALL|ANY|NONE',
                    'Type' => 'ALL|ANY|NONE',
                ],
                // ...
            ],
            'Include' => 'ALL|ANY|NONE',
        ],
        'tags' => ['<string>', ...],
    ],
]);
```

#### Parameter Details, Members
* ApplicationId, Required: Yes, Type: string

### UpdateSegment ( array $params = [] )
* Creates a new segment for an application or updates the configuration, dimension, and other settings for an existing segment that's associated with an application. https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-pinpoint-2016-12-01.html#updatesegment
### 2: Create an endpoint programmatically

### UpdateUserEndpoint 
* Creates a new endpoint for an application or updates the settings and attributes of an existing endpoint for an application. You can also use this operation to define custom attributes for an endpoint. If an update includes one or more values for a custom attribute, Amazon Pinpoint replaces (overwrites) any existing values with the new values.
```
$result = $client->updateUserEndpoint([/* ... */]);
$promise = $client->updateUserEndpointAsync([/* ... */]);
```
Parameter Syntax
```
$result = $client->updateUserEndpoint([
    'ApplicationId' => '<string>', // REQUIRED
    'EndpointId' => '<string>', // REQUIRED
    'EndpointRequest' => [ // REQUIRED
        'Address' => '<string>',
        'Attributes' => [
            '<__string>' => ['<string>', ...],
            // ...
        ],
        'ChannelType' => 'PUSH|GCM|APNS|APNS_SANDBOX|APNS_VOIP|APNS_VOIP_SANDBOX|ADM|SMS|VOICE|EMAIL|BAIDU|CUSTOM|IN_APP',
        'Demographic' => [
            'AppVersion' => '<string>',
            'Locale' => '<string>',
            'Make' => '<string>',
            'Model' => '<string>',
            'ModelVersion' => '<string>',
            'Platform' => '<string>',
            'PlatformVersion' => '<string>',
            'Timezone' => '<string>',
        ],
        'EffectiveDate' => '<string>',
        'EndpointStatus' => '<string>',
        'Location' => [
            'City' => '<string>',
            'Country' => '<string>',
            'Latitude' => <float>,
            'Longitude' => <float>,
            'PostalCode' => '<string>',
            'Region' => '<string>',
        ],
        'Metrics' => [<float>, ...],
        'OptOut' => '<string>',
        'RequestId' => '<string>',
        'User' => [
            'UserAttributes' => [
                '<__string>' => ['<string>', ...],
                // ...
            ],
            'UserId' => '<string>',
        ],
    ],
]);
```

#### Parameter Details
#### Members
* ApplicationId, Required: Yes, Type: string
* EndpointId, Required: Yes, Type: string
* EndpointRequest, Required: Yes, Type: EndpointRequest structure
Specifies the channel type and other settings for an endpoint.

#### Result Syntax
```
[
    'MessageBody' => [
        'Message' => '<string>',
        'RequestID' => '<string>',
    ],
]
```
#### Result Details
#### Members
* MessageBody, Required: Yes, Type: MessageBody structure, Provides information about an API request or response.

#### Errors
* BadRequestException: Provides information about an API request or response.
* InternalServerErrorException: Provides information about an API request or response.
* PayloadTooLargeException: Provides information about an API request or response.
* ForbiddenException: Provides information about an API request or response.
* NotFoundException: Provides information about an API request or response.
* MethodNotAllowedException: Provides information about an API request or response.
* TooManyRequestsException:Provides information about an API request or response.

### UpdateUserEndpointsBatch 
* Creates a new batch of endpoints for an application or updates the settings and attributes of a batch of existing endpoints for an application. You can also use this operation to define custom attributes for a batch of endpoints. If an update includes one or more values for a custom attribute, Amazon Pinpoint replaces (overwrites) any existing values with the new values.
```
$result = $client->updateUserEndpointsBatch([/* ... */]);
$promise = $client->updateUserEndpointsBatchAsync([/* ... */]);
```
#### Parameter Syntax
```
$result = $client->updateUserEndpointsBatch([
    'ApplicationId' => '<string>', // REQUIRED
    'EndpointBatchRequest' => [ // REQUIRED
        'Item' => [ // REQUIRED
            [
                'Address' => '<string>',
                'Attributes' => [
                    '<__string>' => ['<string>', ...],
                    // ...
                ],
                'ChannelType' => 'PUSH|GCM|APNS|APNS_SANDBOX|APNS_VOIP|APNS_VOIP_SANDBOX|ADM|SMS|VOICE|EMAIL|BAIDU|CUSTOM|IN_APP',
                'Demographic' => [
                    'AppVersion' => '<string>',
                    'Locale' => '<string>',
                    'Make' => '<string>',
                    'Model' => '<string>',
                    'ModelVersion' => '<string>',
                    'Platform' => '<string>',
                    'PlatformVersion' => '<string>',
                    'Timezone' => '<string>',
                ],
                'EffectiveDate' => '<string>',
                'EndpointStatus' => '<string>',
                'Id' => '<string>',
                'Location' => [
                    'City' => '<string>',
                    'Country' => '<string>',
                    'Latitude' => <float>,
                    'Longitude' => <float>,
                    'PostalCode' => '<string>',
                    'Region' => '<string>',
                ],
                'Metrics' => [<float>, ...],
                'OptOut' => '<string>',
                'RequestId' => '<string>',
                'User' => [
                    'UserAttributes' => [
                        '<__string>' => ['<string>', ...],
                        // ...
                    ],
                    'UserId' => '<string>',
                ],
            ],
            // ...
        ],
    ],
]);
```

#### Parameter Details
#### Members
* ApplicationId, Required: Yes, Type: string
* EndpointBatchRequest, Required: Yes, Type: EndpointBatchRequest structure : Specifies a batch of endpoints to create or update and the settings and attributes to set or change for each endpoint.
```
Result Syntax
[
    'MessageBody' => [
        'Message' => '<string>',
        'RequestID' => '<string>',
    ],
]
```
#### Result Details
#### Members
* MessageBody, Required: Yes, Type: MessageBody structure: Provides information about an API request or response.

### Errors
* BadRequestException: Provides information about an API request or response.
* InternalServerErrorException: Provides information about an API request or response.
* PayloadTooLargeException: Provides information about an API request or response.
* ForbiddenException: Provides information about an API request or response.
* NotFoundException: Provides information about an API request or response.
* MethodNotAllowedException: Provides information about an API request or response.
* TooManyRequestsException: Provides information about an API request or response.

### UpdateEmailTemplate ( array $params = [] )
* Updates an existing message template for messages that are sent through the email channel. https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-pinpoint-2016-12-01.html#updateemailtemplate
### UpdateSmsChannel ( array $params = [] )
* Enables the SMS channel for an application or updates the status and settings of the SMS channel for an application. https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-pinpoint-2016-12-01.html#updatesmschannel

### UpdateSmsTemplate ( array $params = [] )
* Updates an existing message template for messages that are sent through the SMS channel. https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-pinpoint-2016-12-01.html#updatesmstemplate

### UpdateTemplateActiveVersion ( array $params = [] )
* Changes the status of a specific version of a message template to active. https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-pinpoint-2016-12-01.html#updatetemplateactiveversion

### UpdatePushTemplate ( array $params = [] )
* Updates an existing message template for messages that are sent through a push notification channel. https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-pinpoint-2016-12-01.html#updatepushtemplate

### DeleteEndpoint ( array $params = [] )
* Deletes an endpoint from an application.

## 3. Creating a campaign
### CreateCampaign ( array $params = [] )
* Creates a new campaign for an application or updates the settings of an existing campaign for an application.
```
$result = $client->createCampaign([/* ... */]);
$promise = $client->createCampaignAsync([/* ... */]);
```
#### Parameter Syntax
```
$result = $client->createCampaign([
    'ApplicationId' => '<string>', // REQUIRED
    'WriteCampaignRequest' => [ // REQUIRED
        'AdditionalTreatments' => [
            [
                'CustomDeliveryConfiguration' => [
                    'DeliveryUri' => '<string>', // REQUIRED
                    'EndpointTypes' => ['<string>', ...],
                ],
                'MessageConfiguration' => [
                    'ADMMessage' => [
                        'Action' => 'OPEN_APP|DEEP_LINK|URL',
                        'Body' => '<string>',
                        'ImageIconUrl' => '<string>',
                        'ImageSmallIconUrl' => '<string>',
                        'ImageUrl' => '<string>',
                        'JsonBody' => '<string>',
                        'MediaUrl' => '<string>',
                        'RawContent' => '<string>',
                        'SilentPush' => true || false,
                        'TimeToLive' => <integer>,
                        'Title' => '<string>',
                        'Url' => '<string>',
                    ],
                    'APNSMessage' => [
                        'Action' => 'OPEN_APP|DEEP_LINK|URL',
                        'Body' => '<string>',
                        'ImageIconUrl' => '<string>',
                        'ImageSmallIconUrl' => '<string>',
                        'ImageUrl' => '<string>',
                        'JsonBody' => '<string>',
                        'MediaUrl' => '<string>',
                        'RawContent' => '<string>',
                        'SilentPush' => true || false,
                        'TimeToLive' => <integer>,
                        'Title' => '<string>',
                        'Url' => '<string>',
                    ],
                    'BaiduMessage' => [
                        'Action' => 'OPEN_APP|DEEP_LINK|URL',
                        'Body' => '<string>',
                        'ImageIconUrl' => '<string>',
                        'ImageSmallIconUrl' => '<string>',
                        'ImageUrl' => '<string>',
                        'JsonBody' => '<string>',
                        'MediaUrl' => '<string>',
                        'RawContent' => '<string>',
                        'SilentPush' => true || false,
                        'TimeToLive' => <integer>,
                        'Title' => '<string>',
                        'Url' => '<string>',
                    ],
                    'CustomMessage' => [
                        'Data' => '<string>',
                    ],
                    'DefaultMessage' => [
                        'Action' => 'OPEN_APP|DEEP_LINK|URL',
                        'Body' => '<string>',
                        'ImageIconUrl' => '<string>',
                        'ImageSmallIconUrl' => '<string>',
                        'ImageUrl' => '<string>',
                        'JsonBody' => '<string>',
                        'MediaUrl' => '<string>',
                        'RawContent' => '<string>',
                        'SilentPush' => true || false,
                        'TimeToLive' => <integer>,
                        'Title' => '<string>',
                        'Url' => '<string>',
                    ],
                    'EmailMessage' => [
                        'Body' => '<string>',
                        'FromAddress' => '<string>',
                        'HtmlBody' => '<string>',
                        'Title' => '<string>',
                    ],
                    'GCMMessage' => [
                        'Action' => 'OPEN_APP|DEEP_LINK|URL',
                        'Body' => '<string>',
                        'ImageIconUrl' => '<string>',
                        'ImageSmallIconUrl' => '<string>',
                        'ImageUrl' => '<string>',
                        'JsonBody' => '<string>',
                        'MediaUrl' => '<string>',
                        'RawContent' => '<string>',
                        'SilentPush' => true || false,
                        'TimeToLive' => <integer>,
                        'Title' => '<string>',
                        'Url' => '<string>',
                    ],
                    'InAppMessage' => [
                        'Body' => '<string>',
                        'Content' => [
                            [
                                'BackgroundColor' => '<string>',
                                'BodyConfig' => [
                                    'Alignment' => 'LEFT|CENTER|RIGHT', // REQUIRED
                                    'Body' => '<string>', // REQUIRED
                                    'TextColor' => '<string>', // REQUIRED
                                ],
                                'HeaderConfig' => [
                                    'Alignment' => 'LEFT|CENTER|RIGHT', // REQUIRED
                                    'Header' => '<string>', // REQUIRED
                                    'TextColor' => '<string>', // REQUIRED
                                ],
                                'ImageUrl' => '<string>',
                                'PrimaryBtn' => [
                                    'Android' => [
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                    ],
                                    'DefaultConfig' => [
                                        'BackgroundColor' => '<string>',
                                        'BorderRadius' => <integer>,
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                        'Text' => '<string>', // REQUIRED
                                        'TextColor' => '<string>',
                                    ],
                                    'IOS' => [
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                    ],
                                    'Web' => [
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                    ],
                                ],
                                'SecondaryBtn' => [
                                    'Android' => [
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                    ],
                                    'DefaultConfig' => [
                                        'BackgroundColor' => '<string>',
                                        'BorderRadius' => <integer>,
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                        'Text' => '<string>', // REQUIRED
                                        'TextColor' => '<string>',
                                    ],
                                    'IOS' => [
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                    ],
                                    'Web' => [
                                        'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                        'Link' => '<string>',
                                    ],
                                ],
                            ],
                            // ...
                        ],
                        'CustomConfig' => ['<string>', ...],
                        'Layout' => 'BOTTOM_BANNER|TOP_BANNER|OVERLAYS|MOBILE_FEED|MIDDLE_BANNER|CAROUSEL',
                    ],
                    'SMSMessage' => [
                        'Body' => '<string>',
                        'EntityId' => '<string>',
                        'MessageType' => 'TRANSACTIONAL|PROMOTIONAL',
                        'OriginationNumber' => '<string>',
                        'SenderId' => '<string>',
                        'TemplateId' => '<string>',
                    ],
                ],
                'Schedule' => [
                    'EndTime' => '<string>',
                    'EventFilter' => [
                        'Dimensions' => [ // REQUIRED
                            'Attributes' => [
                                '<__string>' => [
                                    'AttributeType' => 'INCLUSIVE|EXCLUSIVE|CONTAINS|BEFORE|AFTER|BETWEEN|ON',
                                    'Values' => ['<string>', ...], // REQUIRED
                                ],
                                // ...
                            ],
                            'EventType' => [
                                'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                                'Values' => ['<string>', ...], // REQUIRED
                            ],
                            'Metrics' => [
                                '<__string>' => [
                                    'ComparisonOperator' => '<string>', // REQUIRED
                                    'Value' => <float>, // REQUIRED
                                ],
                                // ...
                            ],
                        ],
                        'FilterType' => 'SYSTEM|ENDPOINT', // REQUIRED
                    ],
                    'Frequency' => 'ONCE|HOURLY|DAILY|WEEKLY|MONTHLY|EVENT|IN_APP_EVENT',
                    'IsLocalTime' => true || false,
                    'QuietTime' => [
                        'End' => '<string>',
                        'Start' => '<string>',
                    ],
                    'StartTime' => '<string>', // REQUIRED
                    'Timezone' => '<string>',
                ],
                'SizePercent' => <integer>, // REQUIRED
                'TemplateConfiguration' => [
                    'EmailTemplate' => [
                        'Name' => '<string>',
                        'Version' => '<string>',
                    ],
                    'PushTemplate' => [
                        'Name' => '<string>',
                        'Version' => '<string>',
                    ],
                    'SMSTemplate' => [
                        'Name' => '<string>',
                        'Version' => '<string>',
                    ],
                    'VoiceTemplate' => [
                        'Name' => '<string>',
                        'Version' => '<string>',
                    ],
                ],
                'TreatmentDescription' => '<string>',
                'TreatmentName' => '<string>',
            ],
            // ...
        ],
        'CustomDeliveryConfiguration' => [
            'DeliveryUri' => '<string>', // REQUIRED
            'EndpointTypes' => ['<string>', ...],
        ],
        'Description' => '<string>',
        'HoldoutPercent' => <integer>,
        'Hook' => [
            'LambdaFunctionName' => '<string>',
            'Mode' => 'DELIVERY|FILTER',
            'WebUrl' => '<string>',
        ],
        'IsPaused' => true || false,
        'Limits' => [
            'Daily' => <integer>,
            'MaximumDuration' => <integer>,
            'MessagesPerSecond' => <integer>,
            'Session' => <integer>,
            'Total' => <integer>,
        ],
        'MessageConfiguration' => [
            'ADMMessage' => [
                'Action' => 'OPEN_APP|DEEP_LINK|URL',
                'Body' => '<string>',
                'ImageIconUrl' => '<string>',
                'ImageSmallIconUrl' => '<string>',
                'ImageUrl' => '<string>',
                'JsonBody' => '<string>',
                'MediaUrl' => '<string>',
                'RawContent' => '<string>',
                'SilentPush' => true || false,
                'TimeToLive' => <integer>,
                'Title' => '<string>',
                'Url' => '<string>',
            ],
            'APNSMessage' => [
                'Action' => 'OPEN_APP|DEEP_LINK|URL',
                'Body' => '<string>',
                'ImageIconUrl' => '<string>',
                'ImageSmallIconUrl' => '<string>',
                'ImageUrl' => '<string>',
                'JsonBody' => '<string>',
                'MediaUrl' => '<string>',
                'RawContent' => '<string>',
                'SilentPush' => true || false,
                'TimeToLive' => <integer>,
                'Title' => '<string>',
                'Url' => '<string>',
            ],
            'BaiduMessage' => [
                'Action' => 'OPEN_APP|DEEP_LINK|URL',
                'Body' => '<string>',
                'ImageIconUrl' => '<string>',
                'ImageSmallIconUrl' => '<string>',
                'ImageUrl' => '<string>',
                'JsonBody' => '<string>',
                'MediaUrl' => '<string>',
                'RawContent' => '<string>',
                'SilentPush' => true || false,
                'TimeToLive' => <integer>,
                'Title' => '<string>',
                'Url' => '<string>',
            ],
            'CustomMessage' => [
                'Data' => '<string>',
            ],
            'DefaultMessage' => [
                'Action' => 'OPEN_APP|DEEP_LINK|URL',
                'Body' => '<string>',
                'ImageIconUrl' => '<string>',
                'ImageSmallIconUrl' => '<string>',
                'ImageUrl' => '<string>',
                'JsonBody' => '<string>',
                'MediaUrl' => '<string>',
                'RawContent' => '<string>',
                'SilentPush' => true || false,
                'TimeToLive' => <integer>,
                'Title' => '<string>',
                'Url' => '<string>',
            ],
            'EmailMessage' => [
                'Body' => '<string>',
                'FromAddress' => '<string>',
                'HtmlBody' => '<string>',
                'Title' => '<string>',
            ],
            'GCMMessage' => [
                'Action' => 'OPEN_APP|DEEP_LINK|URL',
                'Body' => '<string>',
                'ImageIconUrl' => '<string>',
                'ImageSmallIconUrl' => '<string>',
                'ImageUrl' => '<string>',
                'JsonBody' => '<string>',
                'MediaUrl' => '<string>',
                'RawContent' => '<string>',
                'SilentPush' => true || false,
                'TimeToLive' => <integer>,
                'Title' => '<string>',
                'Url' => '<string>',
            ],
            'InAppMessage' => [
                'Body' => '<string>',
                'Content' => [
                    [
                        'BackgroundColor' => '<string>',
                        'BodyConfig' => [
                            'Alignment' => 'LEFT|CENTER|RIGHT', // REQUIRED
                            'Body' => '<string>', // REQUIRED
                            'TextColor' => '<string>', // REQUIRED
                        ],
                        'HeaderConfig' => [
                            'Alignment' => 'LEFT|CENTER|RIGHT', // REQUIRED
                            'Header' => '<string>', // REQUIRED
                            'TextColor' => '<string>', // REQUIRED
                        ],
                        'ImageUrl' => '<string>',
                        'PrimaryBtn' => [
                            'Android' => [
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                            ],
                            'DefaultConfig' => [
                                'BackgroundColor' => '<string>',
                                'BorderRadius' => <integer>,
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                                'Text' => '<string>', // REQUIRED
                                'TextColor' => '<string>',
                            ],
                            'IOS' => [
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                            ],
                            'Web' => [
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                            ],
                        ],
                        'SecondaryBtn' => [
                            'Android' => [
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                            ],
                            'DefaultConfig' => [
                                'BackgroundColor' => '<string>',
                                'BorderRadius' => <integer>,
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                                'Text' => '<string>', // REQUIRED
                                'TextColor' => '<string>',
                            ],
                            'IOS' => [
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                            ],
                            'Web' => [
                                'ButtonAction' => 'LINK|DEEP_LINK|CLOSE', // REQUIRED
                                'Link' => '<string>',
                            ],
                        ],
                    ],
                    // ...
                ],
                'CustomConfig' => ['<string>', ...],
                'Layout' => 'BOTTOM_BANNER|TOP_BANNER|OVERLAYS|MOBILE_FEED|MIDDLE_BANNER|CAROUSEL',
            ],
            'SMSMessage' => [
                'Body' => '<string>',
                'EntityId' => '<string>',
                'MessageType' => 'TRANSACTIONAL|PROMOTIONAL',
                'OriginationNumber' => '<string>',
                'SenderId' => '<string>',
                'TemplateId' => '<string>',
            ],
        ],
        'Name' => '<string>',
        'Priority' => <integer>,
        'Schedule' => [
            'EndTime' => '<string>',
            'EventFilter' => [
                'Dimensions' => [ // REQUIRED
                    'Attributes' => [
                        '<__string>' => [
                            'AttributeType' => 'INCLUSIVE|EXCLUSIVE|CONTAINS|BEFORE|AFTER|BETWEEN|ON',
                            'Values' => ['<string>', ...], // REQUIRED
                        ],
                        // ...
                    ],
                    'EventType' => [
                        'DimensionType' => 'INCLUSIVE|EXCLUSIVE',
                        'Values' => ['<string>', ...], // REQUIRED
                    ],
                    'Metrics' => [
                        '<__string>' => [
                            'ComparisonOperator' => '<string>', // REQUIRED
                            'Value' => <float>, // REQUIRED
                        ],
                        // ...
                    ],
                ],
                'FilterType' => 'SYSTEM|ENDPOINT', // REQUIRED
            ],
            'Frequency' => 'ONCE|HOURLY|DAILY|WEEKLY|MONTHLY|EVENT|IN_APP_EVENT',
            'IsLocalTime' => true || false,
            'QuietTime' => [
                'End' => '<string>',
                'Start' => '<string>',
            ],
            'StartTime' => '<string>', // REQUIRED
            'Timezone' => '<string>',
        ],
        'SegmentId' => '<string>',
        'SegmentVersion' => <integer>,
        'TemplateConfiguration' => [
            'EmailTemplate' => [
                'Name' => '<string>',
                'Version' => '<string>',
            ],
            'PushTemplate' => [
                'Name' => '<string>',
                'Version' => '<string>',
            ],
            'SMSTemplate' => [
                'Name' => '<string>',
                'Version' => '<string>',
            ],
            'VoiceTemplate' => [
                'Name' => '<string>',
                'Version' => '<string>',
            ],
        ],
        'TreatmentDescription' => '<string>',
        'TreatmentName' => '<string>',
        'tags' => ['<string>', ...],
    ],
]);
```
#### Parameter Details
#### Members
* ApplicationId, Required: Yes, Type: string

