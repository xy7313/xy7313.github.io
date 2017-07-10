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
- `<apex:commandLink>`
<apex:outputLink> 
<apex:inputFile> 
<apex:inputHidden>
<apex:inputsecret> 
<apex:inputText> 
<apex:inputTextarea>
<apex:inputCheckbox> 
<apex:outputField> 
<apex:outputLabel>
<apex:outputText> 
<apex:pageBlockSectionItem> 
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

