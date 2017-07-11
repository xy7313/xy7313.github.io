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
- `<apex:pageBlockButtons>`
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
- `<apex:inputHidden value="{!inputValue}" id="theHiddenInput"/>` an input element that is invisible to the user. Use this component to pass variables from page to page. eg:`<apex:inputhidden value="{!account.accountNumber}"/>` there is no account number displayed
- `<apex:inputSecret value="{!inputValue}" id="theSecretInput"/>` An HTML input element of type password. eg:`<apex:inputsecret value="{!account.accountNumber}"/>` 
- `<apex:inputText>` ？？ An HTML input element of type text. This component does not use Salesforce styling. Also, since it does not correspond to a field, or any other data on an object, custom code is required to use the value the user inputs.
- `<apex:inputTextarea>` for a value that requires a text area.  eg:`<apex:inputTextarea id="newDesc" value="{!contract.description}"/><p/>  `
- `<apex:inputCheckbox value="{!op.isprivate}"/>`
- `<apex:outputField value="{!opportunity.name}"/>` A read-only display of a label and value for a field
- `<apex:outputLabel>` A label for an input or output field. (similar to inputfield)eg:
```
<apex:outputLabel value="Checkbox" for="theCheckbox"/>
<apex:inputCheckbox value="{!inputValue}" id="theCheckbox"/> 
```
- `<apex:outputText>` Displays text. Displays. You can customize the appearance using CSS styles, in which case the generated text is wrapped in an HTML < span > tag. You can also escape the rendered text if it contains sensitive HTML and XML characters. This component does take localization into account.  ??
```
<apex:page >
    <apex:outputText style="font-style:italic" value="This is {0} text with {1}."> 
        <apex:param value="my"/> 
        <apex:param value="arguments"/>
    </apex:outputText>
</apex:page>
```
- `<apex:pageBlockSectionItem>` 
    - A single piece of data in an < apex:pageBlockSection > that takes up one column in one row. 
    - An < apex:pageBlockSectionItem > component can include up to two child components. 
    - If no content is specified, the column is rendered as an empty space. If one child component is specified, the content spans both cells of the column. If two child components are specified, the content of the first is rendered in the left, "label" cell of the column, while the content of the second is rendered in the right, "data" cell of the column.
    ```
    <apex:pageBlockSectionItem >
          <apex:outputLabel value="Account Type" for="account__type"/>
          <apex:inputText value="{!account.type}" id="account__type"/>
    </apex:pageBlockSectionItem>
    ```
<apex:pageBlockTable> 
<apex:column> 
<apex:dataTable> 
<apex:tabPanel>
<apex:tab> 
<apex:toolbar> 
<apex:toolbarGroup> 
<apex:pageMessage> 
<apex:panelBar> 
<apex:panelBarItem>
<apex:panelGrid>
<apex:panelGroup> 
<apex:param>
<apex:repeat>
<apex:facet>
<apex:actionFunction>
<apex:detail> 
<apex:actionPoller> 
<apex:actionRegion> 
Message Class
<apex:variable>
<apex:stylesheet>
Referencing a Static Resource in Visualforce Pages
<apex:SectionHeader >
<apex:relatedList>
<apex:listViews>
<apex:enhancedList>
<apex:actionStatus> 
<apex:actionSupport>

