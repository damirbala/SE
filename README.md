# SE

Github link to someone: https://github.com/nicoDs96/SE-LABs


SOAP Instructions

Design the service:

create interfaces to define a "contract"
implement interfaces
invoke WS methods from a client.
cfx provides annotations that automatically generate wsdl files and other utilities in order to make the WS usable

Implementation:

Create the endpoint interface with @WebService annotation
1.1 Write down all getters (and / or setters) with a return type not supported by JAXB with an adapter: (optional)
@XmlJavaTypeAdapter (StudentMapAdapter.class)
public Map <String, Integer> getKVPair ();
1.2 Implementing the adapters (optional)

Implement the endpoint interface. Use the annotation:
@WebService (endpointInterface = "com.mycompany.packagetoTheInterface.wsInterface")
Implement the server that runs on a given url for webservice calls:
// this code will host the server
public class Server {
    public static void main (String args []) throws InterruptedException {
        BaeldungImpl implementor = new wsImplementationClass ();
        String address = "http: // localhost: 8080 / wsURL"; // NB specify the protocol or errors may be generated
        Endpoint.publish (address, implementor);
        Thread.sleep (60 * 1000);
        System.exit (0);
    }
}
In NetBeans create a client with the wizard: new project -> ...
On the package click right mouse button -> new -> WebService Client
in the configuration enter the URL specified as the endpoint address with a get request for wsdl:
localhost: 8080 / wsURL? wsdl
