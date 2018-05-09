# validate-saml-metadata

Use the `xmlsectool` and the directory of schema files to validate SAML metadata.

## Install xmlsectool

```bash
cd /tmp
# get xmlsectool
wget http://shibboleth.net/downloads/tools/xmlsectool/latest/xmlsectool-2.0.0-bin.zip
# check hash
shasum ~/Downloads/xmlsectool-2.0.0-bin.zip 
0a624e270f1dfdd913034dfe65a1ec92e8cd8833  /Users/patrick/Downloads/xmlsectool-2.0.0-bin.zip
#
unzip xmlsectool-2.0.0-bin.zip
```

## Validate schema

```
wget https://metdata-ural -O /tmp/metadatafile
export XMLSECPATH=~/Downloads/xmlsectool-2.0.0/
# Assume running from the checkout git repo where schema folder exists
$XMLSECPATH/xmlsectool.sh --validateSchema --schemaDirectory schema --inFile /tmp/metadatafile

INFO  XMLSecTool - Reading XML document from file '/tmp/metadatafile'
INFO  XMLSecTool - XML document parsed and is well-formed.
ERROR XMLSecTool - XML is not schema valid
org.xml.sax.SAXParseException: cvc-complex-type.2.4.a: Invalid content was found starting with element 'md:ArtifactResolutionService'. One of '{"urn:oasis:names:tc:SAML:2.0:metadata":NameIDFormat, "urn:oasis:names:tc:SAML:2.0:metadata":AssertionConsumerService}' is expected.
			       at com.sun.org.apache.xerces.internal.util.ErrorHandlerWrapper.createSAXParseException(ErrorHandlerWrapper.java:203) ~[na:1.8.0_131]
			       at com.sun.org.apache.xerces.internal.util.ErrorHandlerWrapper.error(ErrorHandlerWrapper.java:134) ~[na:1.8.0_131]
			       at com.sun.org.apache.xerces.internal.impl.XMLErrorReporter.reportError(XMLErrorReporter.java:396) ~[na:1.8.0_131]
			       at com.sun.org.apache.xerces.internal.impl.XMLErrorReporter.reportError(XMLErrorReporter.java:327) ~[na:1.8.0_131]
			       at com.sun.org.apache.xerces.internal.impl.XMLErrorReporter.reportError(XMLErrorReporter.java:284) ~[na:1.8.0_131]
			       at com.sun.org.apache.xerces.internal.impl.xs.XMLSchemaValidator$XSIErrorReporter.reportError(XMLSchemaValidator.java:452) ~[na:1.8.0_131]
			       at com.sun.org.apache.xerces.internal.impl.xs.XMLSchemaValidator.reportSchemaError(XMLSchemaValidator.java:3230) ~[na:1.8.0_131]
			       at com.sun.org.apache.xerces.internal.impl.xs.XMLSchemaValidator.handleStartElement(XMLSchemaValidator.java:1790) ~[na:1.8.0_131]
```