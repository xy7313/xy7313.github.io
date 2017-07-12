---
layout: post #post
title: Salesforce Visualforce Page #post title
categories: Salesforce #post category, seperated by space
tags: Salesforce Note #post tag, seperated by space
---


## Visualforce 
- `<apex:page>` creates a visualforce page; all visualforce Tags have to be enclosed in this tag.

- `<apex:page standardController="Account" showHeader="true" tabStyle="account" >`

- `<apex:form>` It's a best practice to have only one < apex:form > tag in a page instead of including it many times

- `<apex:pageblock>` where multiple sections can be created and fields,buttons, tables or links can be displayed. It by default inherits the standard salesforce page style.

- `<apex:pageBlockSection>` 
    - create a section inside a page block, 
    - consists of one or more columns,(default = 2), Each component found in the body of an < apex:pageBlockSection > is placed into the next cell in a row until the number of columns is reached. 

- `<apex:commandButton>` 
    - action that has to be executed when the button is pressed depends on the ACTION attribute specified in this tag
    - always be a child component of the < apex:form > tag. 

- `<apex:pageBlockButtons>` place the buttons on the top or bottom of the page. This can be achieved with the help of this tag. 

- `<apex:inputField>` display fields
    ```
    <apex:form id="changeStatusForm">
        <apex:pageBlock >
            <apex:pageblocksection title="Account Information">
                <apex:inputfield value="{!account.name}"/>
            </apex:pageblocksection>
            <apex:pageblocksection title="Category Information">
                <apex:inputfield value="{!account.type}"/>
            </apex:pageblocksection>
            <apex:pageBlockButtons >
                <apex:commandButton value="Save" action="{!save}"/>
            </apex:pageBlockButtons>
        </apex:pageBlock>
    </apex:form>
    ```

- `<apex:commandlink action="{!save}" value="Save"/>` This tag creates a link that helps to execute an action defined in a controller. 

- `<apex:outputLink>`  creates a link to a URL, the body of it can be text or an image.
 `<apex:outputLink value="https://www.salesforce.com" id="theLink"> www.salesforce.com </apex:outputLink>`

- `<apex:inputFile> ` ？？  A component that creates an input field to upload a file. maximum file size that can be uploaded via Visualforce is 10 MB.
    ```
    <apex:page standardController="Document" extensions="documentExt">
        <apex:messages />
        <apex:form id="theForm">
        <apex:pageBlock >
            <apex:pageBlockSection >
                <apex:inputFile value="{!document.body}"  filename="{!document.name}"/>
                <apex:commandButton value="Save" action="{!save}"/>
            </apex:pageBlockSection>
        </apex:pageBlock>
        </apex:form>
    </apex:page>
    //Controller Class:
    public class documentExt {
        public documentExt(ApexPages.StandardController controller) {
            Document d = (Document) controller.getRecord();
            d.folderid = UserInfo.getUserId(); //this puts it in My Personal Documents
        }                 
    }
    ```

- `<apex:inputHidden value="{!inputValue}" id="theHiddenInput"/>` an input element that is invisible to the user. Use this component to pass variables from page to page. 
    - eg:`<apex:inputhidden value="{!account.accountNumber}"/>` there is no account number displayed

- `<apex:inputSecret value="{!inputValue}" id="theSecretInput"/>` An HTML input element of type password. masked input as user typed
    - eg:`<apex:inputsecret value="{!account.accountNumber}"/>` 

- `<apex:inputText>` ？？ An HTML input element of type text. This component does not use Salesforce styling. Also, since it does not correspond to a field, or any other data on an object, custom code is required to use the value the user inputs.

- `<apex:inputTextarea>` for a value that requires a text area.     - eg:`<apex:inputTextarea id="newDesc" value="{!contract.description}"/><p/>  `

- `<apex:inputCheckbox value="{!op.isprivate}"/>` get user input

- `<apex:outputField value="{!opportunity.name}"/>` A read-only display of a label and value for a field

- `<apex:outputLabel>` A label for an input or output field. (similar to inputfield)eg:
    ```
    <apex:outputLabel value="Checkbox" for="theCheckbox"/>
    <apex:inputCheckbox value="{!inputValue}" id="theCheckbox"/> 
    ```

- `<apex:outputText>` Displays text. Displays. You can customize the appearance using CSS styles, in which case the generated text is wrapped in an HTML < span > tag. You can also escape the rendered text if it contains sensitive HTML and XML characters. This component does take localization into account. There are some example with `param`, `toolbar`, `panalGrid`...

- `<apex:param>` A parameter for the parent component. Within < apex:outputText >, there is support for the < apex:param > tag to match the syntax of the MessageFormat class in Java. Parent components can be:
    - < apex:actionFunction >
    - < apex:actionSupport >
    - < apex:commandButton >
    - < apex:commandLink >
    - < apex:outputLink >
    - < apex:outputText >
    - < flow:interview >
    ```
    <apex:page >
        <apex:outputText style="font-style:italic" value="This is {0} text with {1}."> 
            <apex:param value="my"/> 
            <apex:param value="arguments"/>
        </apex:outputText>
         <apex:outputLink value="http://google.com/search">
            Search Google
            <apex:param name="q" value="{!account.name}"/>
        </apex:outputLink>
        //when we click the link, we search account name in google
    </apex:page>
    ```

- `<apex:pageBlockSectionItem>` 
    - A single piece of data in an < apex:pageBlockSection > that takes up one column in one row. 
    - An < apex:pageBlockSectionItem > component can include up to two child components. 
    - If no content is specified, the column is rendered as an empty space. If one child component is specified, the content spans both cells of the column. If two child components are specified, the content of the first is rendered in the left, "label" cell of the column, while the content of the second is rendered in the right, "data" cell of the column.(like the example below)
    ```
    <apex:pageBlockSectionItem >
          <apex:outputLabel value="Account Type" for="account__type"/>
          <apex:inputText value="{!account.type}" id="account__type"/>
    </apex:pageBlockSectionItem>
    ```

- `<apex:dataTable> ` An HTML table that is defined by iterating over a set of data, displaying information about one item of data per row. The set of data can contain up to 1,000 items.
    ```
    <apex:page standardController="Lead" recordSetVar="Leads">
        <apex:pageBlock title="dataTable">
            <apex:dataTable value="{!Leads}" var="le" width="50%">
                <apex:column value="{!le.name}"  headerValue="Name"/> 
                <apex:column value="{!le.Phone}" headerValue="Phone"/>
                <apex:column value="{!le.Company}" headerValue="Company"/>
            </apex:dataTable> 
        </apex:pageBlock> 
    </apex:page>
    ```

- `<apex:pageBlockTable>` 
    - A list of data displayed as a table
    - within either an < apex:pageBlock > or < apex:pageBlockSection > component
    - similar to a related list or list view in a standard Salesforce page
    -  Like an < apex:dataTable>, an < apex:pageBlockTable > is defined by iterating over a set of data, displaying information about one item of data per row. The set of data can contain up to 1,000 items.
        ```
        <apex:page standardController="Lead" recordSetVar="Leads">
            <apex:pageBlock title="pageBlockTable">
                <apex:pageBlockTable value="{!Leads}" var="le">
                    <apex:column value="{!le.name}"/> 
                    <apex:column value="{!le.Phone}"/>
                    <apex:column value="{!le.Company}"/>
                </apex:pageBlockTable> 
            </apex:pageBlock> 
        </apex:page>
        //this example shows all leads in a table with name, phone and company fields
        ```

- `<apex:column>` must always be a child of an < apex:dataTable > or < apex:pageBlockTable > component.

- `<apex:facet>` A placeholder for content that is rendered in a specific part of the parent component, such as the header or footer of an < apex:dataTable >.(it's like the column name). An < apex:facet > component can only exist in the body of a parent component if the parent supports facets.
    ```
    <apex:page standardController="Account">
        <apex:pageBlock title="Contacts">
            <apex:dataTable value="{!account.Contacts}" var="contact" cellPadding="4" border="1">
                <apex:column>
                    <apex:facet name="header">Name</apex:facet>
                            {!contact.Name}
                </apex:column>
                <apex:column>
                    <apex:facet name="header">Phone</apex:facet>
                            {!contact.Phone}
                </apex:column>
            </apex:dataTable>
        </apex:pageBlock>
    </apex:page>
    ```

- `<apex:tabPanel>`  A page area that displays as a set of tabs. When a user clicks a tab header, the tab's associated content displays, hiding the content of other tabs.

- `<apex:tab>` A single tab in an < apex:tabPanel>. The <apex:tab> component must be a child of a < apex:tabPanel >. 
    ```
    <apex:page id="thePage">
        <apex:tabPanel switchType="client" selectedTab="name2" id="theTabPanel">
            <apex:tab label="One" name="name1" id="tabOne">content for tab one</apex:tab>
            <apex:tab label="Two" name="name2" id="tabTwo">content for tab two</apex:tab>
        </apex:tabPanel>
    </apex:page>
    ```

- `<apex:toolbar> `A stylized, horizontal toolbar that can contain any number of child components. By default, all child components are aligned to the left side of the toolbar. Use an 
 <apex:toolbarGroup> component to align one or more child components to the right.

- `<apex:toolbarGroup> ` A group of components within a toolbar that can be aligned to the left or right of the toolbar.
    ```
    <apex:page id="thePage">
        <apex:toolbar id="theToolbar">
            <apex:outputText value="Sample Toolbar"/>
            <apex:toolbarGroup itemSeparator="line" id="toobarGroupLinks">
                <apex:outputLink value="http://www.salesforce.com">salesforce </apex:outputLink>
                <apex:outputLink value="http://developer.salesforce.com">apex developer network </apex:outputLink>
            </apex:toolbarGroup>
            <apex:toolbarGroup itemSeparator="line" location="right" id="toobarGroupForm">
            <apex:form id="theForm">
                    <apex:inputText id="theInputText">Enter Text</apex:inputText>
                    <apex:commandLink value="search" id="theCommandLink"/>
                </apex:form>
            </apex:toolbarGroup>
        </apex:toolbar>
    </apex:page>
    ```

- `<apex:pageMessage>` This component should be used for presenting custom messages in the page using the Salesforce pattern for errors, warnings and other types of messages for a given severity.
    - e.g.: `<apex:pageMessage summary="This pageMessage will always display. Validation error messages appear in the pageMessages component." severity="warning" strength="3" />`

- `<apex:panelBar>` 
    - A page area that includes one or more < apex:panelBarItem > tags that can expand when a user clicks the associated header. 
    - An < apex:panelBar > can include up to 1,000 < apex:panelBarItem > tags.
    - When an < apex:panelBarItem > is expanded, the header and the content of the item are displayed while the content of all other items are hidden. When another < apex:panelBarItem > is expanded, the content of the original item is hidden again. 
    ```
    <apex:page >
        <apex:panelBar >
        <apex:panelBarItem label="Item1">data1</apex:panelBarItem>
        <apex:panelBarItem label="Item2">data2</apex:panelBarItem>
            <apex:panelBarItem label="Item3">data3            </apex:panelBarItem>
        </apex:panelBar>
    </apex:page>
    ```
- `<apex:panelBarItem>` 

- `<apex:panelGrid>` each component found in the body of the 
< apex:panelGrid > is placed into a corresponding cell in the first row until the number of columns is reached. At that point, the next component wraps to the next row and is placed in the first cell.
    - eg: it shows like: (line one): First Second Third; (line two): Fourth
    ```
    <apex:page >
        <apex:panelGrid columns="3" id="theGrid">
            <apex:outputText value="First" id="theFirst"/>
            <apex:outputText value="Second" id="theSecond"/>
            <apex:outputText value="Third" id="theThird"/>
            <apex:outputText value="Fourth" id="theFourth"/>
        </apex:panelGrid>
    </apex:page>
    ```

- `<apex:panelGroup> `A container for multiple child components so that they can be displayed in a single panelGrid cell. An < apex:panelGroup > must be a child component of an < apex:panelGrid >.
    - eg: it shows like: (line one): First Second ThirdFourth
    ```
    <apex:page >
        <apex:panelGrid columns="3" id="theGrid">
            <apex:outputText value="First" id="theFirst"/>
            <apex:outputText value="Second" id="theSecond"/>
            <apex:panelGroup id="theGroup">
                <apex:outputText value="Third" id="theThird"/>
                <apex:outputText value="Fourth" id="theFourth"/>
            </apex:panelGroup>
        </apex:panelGrid>
    </apex:page>
    ```

- `<apex:repeat>` An iteration component that allows you to output the contents of a collection according to a structure that you specify. The collection can include up to 1,000 items.
    -  if used within an < apex:pageBlockSection > or < apex:panelGrid > component, all content generated by a child < apex:repeat > component is placed in a single < apex:pageBlockSection > or < apex:panelGrid > cell.
    - attributes: 
        - first: For example, if you did not want to display the first two elements in the set of records specified by the value attribute, set first="2".
        - value: The collection of data that is iterated over.
        - var: The name of the variable that represents the current item in the iteration.
    ```
    <apex:page controller="repeatCon" id="thePage">
        <apex:repeat value="{!strings}" var="string" id="theRepeat">
            <apex:outputText value="{!string}" id="theValue"/> 
            <br/>
        </apex:repeat>
    </apex:page>
    //Controller class:
    public class repeatCon {
        public String[] getStrings() {
            return new String[]{'ONE','TWO','THREE'};
        }
    }
    ```

<apex:actionPoller> 
<apex:actionRegion> 
<apex:actionFunction>

-  `<apex:detail>` The standard detail page for a particular object, as defined by the associated page layout for the object in Setup. eg:`<apex:detail subject="{!account.ownerId}" relatedList="false" title="false"/>`
- Message Class
    - If your application uses a custom controller or extension, you must use the message class for collecting errors.
    - ApexPages.severity is the enum that is determines how severe a message is
    ```
    ApexPages.Message myMsg = new ApexPages.Message(ApexPages.Severity.FATAL, 'my error msg');
    ApexPages.Message myMsg = new ApexPages.Message(ApexPages.severity, summary, detail);
    ```
- page reference class (when using custom controller or controller extension)
    - `Page.existingPageName   ` By referring to a page in this way, the platform recognizes that this controller or controller extension is dependent on the existence of the specified page and will prevent the page from being deleted while the controller or extension exists. 
    - `PageReference pageRef = new PageReference('partialURL');`   For example, setting 'partialURL' to'/apex/HelloWorld', setting 'partialURL' to '/' + 'recordID' 
        - (less preferable!!) because the PageReference is constructed at runtime, rather than referenced at compile time. Runtime references are not available to the referential integrity system. Consequently, the platform doesn't recognize that this controller or controller extension is dependent on the existence of the specified page and won't issue an error message to prevent user deletion of the page.
    -  `PageReference pageRef = new PageReference('http://www.google.com');` creates a page reference for an external URL
    - `PageReference pageRef = ApexPages.currentPage();` instantiate a PageReference object for the current page with the currentPage ApexPages method. 
- Select Option Class:
    - A SelectOption can also be displayed in a disabled state, so that a user cannot select it as an option, but can still view it.
    - exanple: where values is the String that is returned to the controller if the option is selected by a user,label is the String that is displayed to the user as the option choice, and Disabled is a Boolean that, if true, specifies that the user cannot select the option, but can still view it.
    ```
    SelectOption option = new SelectOption(value, label, isDisabled);
    ```
- Standard Controller Class: The only time it is necessary to refer to a StandardController object is when defining an extension for a standard controller. StandardController is the data type of the single argument in the extension class constructor.
`ApexPages.StandardController sc = new ApexPages.StandardController(sObject);`
<apex:variable>
<apex:stylesheet>
Referencing a Static Resource in Visualforce Pages
<apex:SectionHeader >
<apex:relatedList>
<apex:listViews>
<apex:enhancedList>
<apex:actionStatus> 
<apex:actionSupport>

