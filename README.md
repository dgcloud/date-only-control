# Alfresco date-only-control

An Alfresco Share form control to "fix" problems with date-only properties and daylight saving time. 

The problem is described at [serious date/time problems in Alfresco](https://hub.alfresco.com/t5/alfresco-content-services-forum/serious-date-time-problems-in-alfresco/td-p/139647)   

What the form control does is to send the time part, even for the date-only properties, using a fixed value (sample below).

# Packaging the project

To package this module use `mvn clean install -DskipTests=true`.

Use the generated amp file to deploy on Share using the alfresco-mmt.jar file as described at [Installing an Alfresco Module Package](https://docs.alfresco.com/community/tasks/amp-install.html)

# How to use it

In order to aply the "fix" for the date properties, simply configure the field with share-config-custom.xml, as the sample below:

```
<field id="san:dataDe">
    <control template="/form-controls/date-only.ftl">
        <control-param name="submitTime">true</control-param>
        <control-param name="fixedTime">12:00:00.000-00:00</control-param>
    </control>
</field>
```