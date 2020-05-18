
public class Animallocator {
    
public static String getAnimalNameById(Integer Id) {
		Http http = new Http();
		HttpRequest request = new HttpRequest();
		request.setEndpoint('https://th-apex-http-callout.herokuapp.com/animals/' + id);
		request.setMethod('GET');
		HttpResponse response = http.send(request);
		String strResp = '';
		system.debug('*******response' +response.getStatusCode());
		system.debug('*******response' +response.getBody());
		if (response.getstatuscode()==200)
		{
			Map<String, object> results = (Map<String, Object>) JSON.deserializeUntyped(response.getBody());
			Map<String, object> animals = (Map<String, Object>) (results.get('animal');
			System.debug('Received the following animals:' + animals);
			strResp =string.valueof (animals.get('name'));
			System.debug('strResp >'+strResp);
		}                                                              
		return strResp;
	}                                                              
}                                                              
