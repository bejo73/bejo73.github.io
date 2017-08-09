Om man i ett 'Expression' vill hämta ett värde från ett XML-dokument så kan man använda sig av funktionen xpath.

value = xpath(xmlDocument, "string(/*[local-name()='Message']/Body/Element)");
