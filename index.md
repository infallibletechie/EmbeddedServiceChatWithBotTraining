<html>
<style type='text/css'>
	.embeddedServiceHelpButton .helpButton .uiButton {
		background-color: #005290;
		font-family: "Arial", sans-serif;
	}
	.embeddedServiceHelpButton .helpButton .uiButton:focus {
		outline: 1px solid #005290;
	}
</style>

<script type='text/javascript' src='https://service.force.com/embeddedservice/5.0/esw.min.js'></script>
<script type='text/javascript'>
	var initESW = function(gslbBaseURL) {
		embedded_svc.settings.displayHelpButton = true; //Or false
		embedded_svc.settings.language = ''; //For example, enter 'en' or 'en-US'

		embedded_svc.settings.enabledFeatures = ['LiveAgent'];
		embedded_svc.settings.entryFeature = 'LiveAgent';
	
		window.addEventListener("message", receiveMessage, false);
			function receiveMessage(event) {
			var payload = event.data;

			if(payload && payload.type === "chasitor.sendMessage") {
				embedded_svc.postMessage("chasitor.sendMessage", payload.message);
			}
		};

		embedded_svc.init(
			'https://test-ec-dev-ed.develop.my.salesforce.com',
			'https://test-ec-dev-ed.develop.my.site.com/',
			gslbBaseURL,
			'00D3t000005YGES',
			'Embedded_Service_Deployment_With_Bot',
			{
				baseLiveAgentContentURL: 'https://c.la1-c1-ia4.salesforceliveagent.com/content',
				deploymentId: '5723t000000DIAE',
				buttonId: '5733t00000096rS',
				baseLiveAgentURL: 'https://d.la1-c1-ia4.salesforceliveagent.com/chat',
				eswLiveAgentDevName: 'EmbeddedServiceLiveAgent_Parent04I3t000000LR07EAG_18802399dbe',
				isOfflineSupportEnabled: false
			}
		);
	};

	if (!window.embedded_svc) {
		var s = document.createElement('script');
		s.setAttribute('src', 'https://test-ec-dev-ed.develop.my.salesforce.com/embeddedservice/5.0/esw.min.js');
		s.onload = function() {
			initESW(null);
		};
		document.body.appendChild(s);
	} else {
		initESW('https://service.force.com');
	}
</script>  
</html>
