PaylifeSMS API

PaylifeSMS API is build for PaylifeSMS - Bulk SMS Application For Marketing
Prerequisites

php >=5.6
PaylifeSMS - Bulk SMS Application For Markting

Installing



git clone https://github.com/matsaina/Paylife-sms-api.git

Usage
Step 1:

If install PaylifeSMS API using Git Clone then load your PaylifeSMS API Class file and Use namespace.

require_once 'src/Class_Ultimate_SMS_API.php';
use PaylifeSMS\PaylifeSMSAPI;

If install PaylifeSMS API using Composer then Require/Include autoload.php file in the index.php of your project or whatever file you need to use PaylifeSMS API classes:.

require 'vendor/autoload.php';
use UltimateSMS\UltimateSMSAPI;

Step 2:

set your API_KEY from https://mywebhost.com/sms-api/info (your application install url)

$api_key = 'YWRtaW46YWRtaW4ucGFzc3dvcmQ=';

Step 3:

Change the from number below. It can be a valid phone number or a String

$from = '254721000000';

Step 4:

the number we are sending to - Any phone number

$destination = '254721111111';

For multiple number please use Comma (,) after every single number.

$destination = '254721111111,254721222222,254721333333,254721444444';

You can insert maximum 100 numbers using comma in single api request.

You have to must include Country code at beginning of the phone number.
Step 5:

Replace your Install URL like https://mywebhost.com/sms/api with https://ultimatesms.coderpixel.com/demo/ sms/api is mandatory on your install url

$url = 'https://portal.paylifesms.com/sms/api';

// SMS Body

$sms = 'test message from Paylifesms';

// Unicode SMS

$unicode = '1'; //For Unicode message

// Voice SMS

$voice = '1'; //For voice message

// MMS SMS

$mms = '1'; //For mms message
$media_url = 'https://yourmediaurl.com'; //Insert your media url

// Schedule SMS

$schedule_date = '09/17/2018 10:20 AM'; //Date like this format: m/d/Y h:i A

// Create Plain/text SMS Body for request

$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms
);

// Create Unicode SMS Body for request

$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'unicode' => $unicode,
);

// Create Voice SMS Body for request

$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'voice' => $voice,
);

// Create MMS SMS Body for request

$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms, //optional
    'mms' => $mms,
    'media_url' => $media_url,
);

// Create Schedule SMS Body for request

$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'schedule' => $schedule_date,
);

Step 6:

Instantiate a new PaylifeSMS API request

$client = new PaylifeSMSAPI();

Send SMS

Finally send your sms through PaylifeSMS API

$response = $client->send_sms($sms_body, $url);

Get Inbox

Get your all message

$get_inbox=$client->get_inbox($api_key,$url);

Get Balance

Get your account balance

$get_balance=$client->check_balance($api_key,$url);

Response

PaylifeSMS API return response with json format, like:

{"code":"ok","message":"Successfully Send"}

Status Code
Status 	Message
ok 	Successfully Send
100 	Bad gateway requested
101 	Wrong action
102 	Authentication failed
103 	Invalid phone number
104 	Phone coverage not active
105 	Insufficient balance
106 	Invalid Sender ID
107 	Invalid SMS Type
108 	SMS Gateway not active
109 	Invalid Schedule Time
110 	Media url required
111 	SMS contain spam word. Wait for approval
