# XML
* XMLstands for eXtensible Markup Language
* XML was designed to store and transport data
* XML was designed to be both human- and machine-readable
* XML Documents Must Have Exactly One Root Element/Tag
* White-space is Preserved in XML (XML does not truncate multiple white-spaces)
* XML Stores New Line as LF
 * Windows applications store a new line as: carriage return and line feed (CR+LF).
 * Unix and Mac OSX use LF.
 * Old Mac systems use CR.
 * XML stores a new line as LF.


* Example:
      <?xml version="1.0" encoding="UTF-8"?>
      <note>
       <to>Tove</to>
       <from>Jani</from>
       <heading>Reminder</heading>
       <body>Don't forget me this weekend!</body>
      </note>

## The XML Prolog
    <?xml version="1.0" encoding="UTF-8"?>
The XML prolog is optional. If it exists, it must come first in the document
* The XML prolog does not have a closing tag!. The prolog is not a part of the XML document


## XML Elements/Tags
* XML tags are case sensitive i.e. <root> and <Root> both tags are different
* XML allows creating new tags (user defined tags)
* All XML Elements Must Have a Closing Tag
* XML Attribute Values Must Always be Quoted
      <note date="12/11/2007">
        <to>Tove</to>
        <from>Jani</from>
      </note>
* aaaa


## Characters that have a special meaning:
Only < and & are strictly illegal in XML, but it is a good habit to replace > with &gt; as well

|chracter|entity reference|character name|
|--------|----------------|--------------|
|<       |     `&lt;`     | less than    |
|>       |     `&gt;`     | greater than |
|&       |    `&amp;`     | ampersand    |
|'       |    `&apos;`    | apostrophe   |
|"       |    `&quot;`    |quotation mark|


## Comments in XML
    <!-- This is a comment -->


Two dashes in the middle of a comment are not allowed:

    <!-- This is an invalid -- comment -->
