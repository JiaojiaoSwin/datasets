# Datasets
machine generated messages

DataSet | Protocol | Files | Format | Notes
---|---|---|---|--
LDAP (binary) | LDAP | [ldap_traffic_20140123.json](ldap_traffic_20140123.json) | JSON | Binary LDAP trace
LDAP (text) | LDAP | [ldap_traffic_20140123.json](ldap_traffic_20140123.json) | JSON | Textually formated LDAP messages
Twitter | Twitter (REST) | n/a | n/a | Status IDs of dataset are available on request
IMS | IMS | [ims_100.json](ims_100.json) | JSON | IBM Information Management System message trace
Banking Application | SOAP | [ims_100.json](ims_100.json) | JSON | Banking application message trace
Logparser SOSP | log files | [SOSP.json](SOSP.json) | JSON | Logparser SOSP log files
Proxifier | log files | [Proxifier.json](Proxifier.json) | JSON | Proxifier log files

## JSON format of files

The message trace and log files are stored in a JSON file containing a list of string arrays.
i.e. Expressed as a Java type:

List<String[]>

Each item in the list contains a request followed by zero or more responses.

The files may be read using the [json-io](https://github.com/jdereg/json-io) Json Reader. The following code snippet shows how the JSON files may be read in Java:

```
import com.cedarsoftware.util.io.JsonReader;

...

    public static final List<String[]> readJsonPairs(String msgfile)
        throws IOException
    {
        FileInputStream fis = new FileInputStream(msgfile);
        JsonReader jr = new JsonReader(fis);
        List<String[]> messages = (List<String[]>)jr.readObject();
        jr.close();
        fis.close();
        return messages;
    }
```
