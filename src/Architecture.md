![[Flutter_Architecture.png]]
![[Domain_Layer.png]]
1. Contains Model of classes
2. Abstraction of services 
3. Eg. ![[Domain_Model_AbstractService.png]]
![[Infrastructure_layer.png]]
1. Communicate to Remote Data Sources
2. Communicate to Local Data Sources
3. Handle Serialisation and De-serialisation of the data
	- Serialisation: Conversion of Object to Json.
	- Deserialisation: Conversion of Json to Object
	- Process: Serialisation: Object-> converted to Map -> encode ->Json
	- Process: De-serialisation: Json-> converted to Map -> decode ->Object
	- ![[Serialise_De-serialise.png]]
![[Presentation_layer.png]]
1. Minimum UI Rebuilds for better performance that enables higher framer per second
2. Avoiding Full page Rebuild 
	- If you have a complex page and only a text have to change in that condition full UI rebuilds should be avoided
![[Application_Layer.png]]
1. Handle state Management