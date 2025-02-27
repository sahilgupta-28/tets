#Main Diagram
Generated using [DbSchema](https://dbschema.com)




### Main Diagram
![img](./MainDiagram.svg)



### Collection dev-jt.attachments 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
|  | type| string  |
|  | name| string  |
| &#128270; | attachment| string  |
|  | attachmentKey| string  |
| &#11016; | invoice| objectId  |
| &#128270; &#11016; | quotationJob| objectId  |
| &#11016; | company| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | folder| objectId  |
|  | updatedBy| objectId  |
|  | deletedBy| objectId  |
| &#11016; | addedBy| objectId  |
| &#128270; | isDefault| Boolean  |
|  | fileSize| string  |
|  | fileExtension| string  |
| &#128270; &#11016; | workOrder| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDefault\_1 | ON isDefault|
| &#128270;  | quotationJob\_1 | ON quotationJob|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | workOrder\_1 | ON workOrder|
| &#128270;  | attachment\_1 | ON attachment|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( folder ) ref [dev-jt.attachments](#attachments) (\_id) |
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( invoice ) ref [dev-jt.invoices](#invoices) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( workOrder ) ref [dev-jt.workorders](#workorders) (\_id) |




### Collection dev-jt.calendars 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | title| string  |
| * | location| string  |
| * | allDay| Boolean  |
| * | start| date  |
| * | end| date  |
| * | startTime| string  |
| * | endTime| string  |
| * | reminder| object  |
| * | reminder.date| date  |
| * | reminder.isSent| Boolean  |
| * | note| string  |
| * | label| string  |
| * | to| array  |
| * &#11016; | event| objectId  |
| * &#11016; | quotationJob| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * | isSystem| Boolean  |
| * | isActive| Boolean  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | \_\_v| int  |
| * | createdAt| date  |
| * | updatedAt| date  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( event ) ref [dev-jt.events](#events) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.clients 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | firstName| string  |
|  | companyName| string  |
| * | email| string  |
| * | phoneNumber| string  |
| * | address| object  |
|  | address.location| string  |
| * | address.street| string  |
|  | address.unit| string  |
| * | address.city| string  |
| * | address.state| string  |
| * | address.pincode| string  |
| * &#128270; &#11016; | company| objectId  |
| &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | lastName| string  |
| &#11016; | updatedBy| objectId  |
| &#128270; | imported| Boolean  |
|  | quickbookClientId| string  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | imported\_1 | ON imported|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.companies 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
|  | name| string  |
| * | image| string  |
| * | subscription| object  |
| * | subscription.validTo| date  |
| * | subscription.status| string  |
| * | subscription.validFrom| date  |
|  | subscription.activeDate| date  |
|  | subscription.updatedAt| date  |
|  | subscription.cancelledDate| date  |
|  | subscription.extendDate| date  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#128270; &#11016; | userDetail| objectId  |
|  | stripe| object  |
| * | stripe.customer| string  |
|  | stripe.subscription| string  |
|  | imageKey| string  |
|  | address| object  |
|  | address.location| string  |
|  | address.street| string  |
|  | address.unit| string  |
|  | address.city| string  |
|  | address.state| string  |
|  | address.country| string  |
|  | address.pincode| string  |
|  | phoneNumber| string  |
|  | website| string  |
|  | isDisabled| Boolean  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | userDetail\_1 | ON userDetail|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( userDetail ) ref [dev-jt.companies](#companies) (\_id) |




### Collection dev-jt.customforms 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | name| string  |
| * &#128270; &#11016; | company| objectId  |
| * | html| string  |
| * | json| array[object]  |
| * | json.type| string  |
| * | json.label| string  |
| * | json.id| string  |
|  | json.placeHolder| string  |
|  | json.icons| object  |
|  | json.icons.todoIcon| object  |
|  | json.icons.todoIcon.src| string  |
|  | json.icons.todoIcon.height| int  |
|  | json.icons.todoIcon.width| int  |
|  | json.icons.todoIcon.blurWidth| int  |
|  | json.icons.todoIcon.blurHeight| int  |
|  | json.icons.todoIcon.type| string  |
|  | json.icons.todoIcon.icon| object  |
| * | json.icons.todoIcon.icon.src| string  |
| * | json.icons.todoIcon.icon.height| int  |
| * | json.icons.todoIcon.icon.width| int  |
| * | json.icons.todoIcon.icon.blurWidth| int  |
| * | json.icons.todoIcon.icon.blurHeight| int  |
| * | json.icons.taskIcon| array[object]  |
|  | json.icons.taskIcon.icon| object  |
| * | json.icons.taskIcon.icon.src| string  |
| * | json.icons.taskIcon.icon.height| int  |
| * | json.icons.taskIcon.icon.width| int  |
| * | json.icons.taskIcon.icon.blurWidth| int  |
| * | json.icons.taskIcon.icon.blurHeight| int  |
|  | json.icons.taskIcon.type| string  |
|  | json.icons.taskIcon.src| string  |
|  | json.icons.taskIcon.height| int  |
|  | json.icons.taskIcon.width| int  |
|  | json.icons.taskIcon.blurWidth| int  |
|  | json.icons.taskIcon.blurHeight| int  |
|  | json.required| Boolean  |
|  | json.className| string  |
|  | json.name| string  |
|  | json.access| Boolean  |
|  | json.subtype| string  |
|  | json.value| string  |
|  | json.isRequired| string  |
|  | json.multiple| Boolean  |
|  | json.values| array[object]  |
| * | json.values.label| string  |
|  | json.values.value| string  |
| * | json.values.selected| Boolean  |
| * | json.values.id| string  |
|  | json.bgColor| string  |
|  | json.color| string  |
|  | json.style| string  |
|  | json.buttonType| string  |
|  | json.placeholder| string  |
|  | json.btnAlignment| string  |
|  | json.inline| Boolean  |
|  | json.other| Boolean  |
|  | json.isNew| Boolean  |
|  | json.isDefaultField| Boolean  |
|  | json.isDefault| Boolean  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |
| &#11016; | updatedBy| objectId  |
|  | alignment| string  |
|  | showFormName| Boolean  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.eventlabels 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | name| string  |
|  | color| string  |
| * &#11016; | company| objectId  |
| * | isActive| Boolean  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | deletedBy| objectId  |
| &#11016; | updatedBy| objectId  |
| &#11016; | addedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.events 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | title| string  |
| * | location| string  |
| * | allDay| Boolean  |
| * | start| date  |
| * | end| date  |
| * | startTime| string  |
| * | endTime| string  |
| * | timeDiff| object  |
| * | reminder| object  |
| * | reminder.date| date  |
|  | reminder.isSent| Boolean  |
| * | note| string  |
| * &#11016; | label| string  |
| * | to| array  |
| * &#11016; | quotationJob| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * | isSystem| Boolean  |
| * | isActive| Boolean  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | updatedBy| objectId  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |
| &#11016; | assignedMembers| array[objectid]  |
| &#11016; | client| objectId  |
|  | isRecurring| Boolean  |
| &#11016; | parentId| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | company\_1 | ON company|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( client ) ref [dev-jt.clients](#clients) (\_id) |
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( label ) ref [dev-jt.eventlabels](#eventlabels) (\_id) |
| Vir | Relationship | ( parentId ) ref [dev-jt.events](#events) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( assignedMembers ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.googleemaildetails 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|



### Collection dev-jt.histories 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | type| string  |
| * | action| string  |
| * | title| string  |
| * &#128270; &#11016; | invoice| objectId  |
| * &#128270; &#11016; | quotationJob| objectId  |
| * &#11016; | company| objectId  |
| * &#128270; &#11016; | user| objectId  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#128270; | workOrder| string  |
| &#128270; | jobCost| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | quotationJob\_1 | ON quotationJob|
| &#128270;  | user\_1 | ON user|
| &#128270;  | invoiceLineItem\_1 | ON invoice|
| &#128270;  | workOrder\_1 | ON workOrder|
| &#128270;  | jobCost\_1 | ON jobCost|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( invoice ) ref [dev-jt.invoices](#invoices) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( user ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.invoicelineitems 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | label| string  |
| * | description| string  |
| * | amount| object  |
| &#11016; | invoiceLineItem| objectId  |
|  | subLineItems| array[object]  |
| * | subLineItems.label| string  |
| * | subLineItems.description| string  |
| * | subLineItems.amount| object  |
| * | subLineItems.isInvoiceFull| Boolean  |
| * | subLineItems.subSubLineItems| array[object]  |
| * | subLineItems.subSubLineItems.label| string  |
| * | subLineItems.subSubLineItems.amount| object  |
| * | subLineItems.subSubLineItems.type| string  |
| * | subLineItems.subSubLineItems.quantity| object  |
| * | subLineItems.subSubLineItems.totalAmount| object  |
| * | subLineItems.subSubLineItems.\_id| objectId  |
|  | subLineItems.subSubLineItems.invoicedToDate| object  |
|  | subLineItems.subSubLineItems.markup| int  |
| * | subLineItems.\_id| objectId  |
|  | subLineItems.discount| object  |
| * | subLineItems.discount.type| string  |
| * | subLineItems.discount.amount| string  |
| * | subLineItems.discount.description| string  |
| * | subLineItems.discount.totalDiscount| object  |
|  | subLineItems.invoiceRemaining| object  |
|  | subLineItems.subLineItem| objectId  |
|  | subLineItems.finalAmount| object  |
| &#128270; &#11016; | invoice| objectId  |
| &#11016; | job| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | \_\_v| int  |
| * | createdAt| date  |
| * | updatedAt| date  |
|  | finalAmount| object  |
|  | markup| int  |
|  | lineIndex| int  |
|  | discount| object  |
| * | discount.type| string  |
| * | discount.amount| string  |
| * | discount.description| string  |
| * | discount.totalDiscount| object  |
|  | invoicedToDate| object  |
|  | invoiceRemaining| object  |
|  | taxDetail| object  |
| * | taxDetail.number| string  |
| * | taxDetail.name| string  |
| * | taxDetail.rate| object  |
| * | taxDetail.totalTax| object  |
| &#128270; | isOptionalItem| Boolean  |
| &#128270; | isHoldback| Boolean  |
| &#128270; | isInvoiceHoldback| Boolean  |
| &#128270; | extra| Boolean  |
|  | quoteDiscount| object  |
| * | quoteDiscount.type| string  |
| * | quoteDiscount.amount| string  |
| * | quoteDiscount.description| string  |
| * | quoteDiscount.totalDiscount| object  |
| &#11016; | deletedBy| objectId  |
| &#11016; | updatedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isOptionalItem\_1 | ON isOptionalItem|
| &#128270;  | isHoldback\_1 | ON isHoldback|
| &#128270;  | isInvoiceHoldback\_1 | ON isInvoiceHoldback|
| &#128270;  | extra\_1 | ON extra|
| &#128270;  | invoice\_1 | ON invoice|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( invoiceLineItem ) ref [dev-jt.invoicelineitems](#invoicelineitems) (\_id) |
| Vir | Relationship | ( invoice ) ref [dev-jt.invoices](#invoices) (\_id) |
| Vir | Relationship | ( job ) ref [dev-jt.jobs](#jobs) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.invoicepayments 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | date| string  |
| * | amount| object  |
| * | paymentMethod| string  |
| * | checkNumber| string  |
| * &#128270; &#11016; | invoice| objectId  |
| * &#11016; | addedBy| objectId  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | company| objectId  |
|  | withoutTaxAmount| object  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | invoice\_1 | ON invoice|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( invoice ) ref [dev-jt.invoices](#invoices) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.invoices 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| &#128270; | invoiceId| string  |
| * &#128270; | type| string  |
| * | paymentDue| object  |
| * | paymentDue.reminderSent| Boolean  |
|  | paymentDue.days| int  |
|  | paymentDue.date| date  |
|  | paymentDue.reminderDate| date  |
| * | reminder| object  |
| * | reminder.isSent| Boolean  |
|  | reminder.isSecondSent| Boolean  |
|  | reminder.date| date  |
|  | reminder.secondDate| date  |
| * | status| string  |
| * | isJobDraft| Boolean  |
| * &#128270; &#11016; | client| objectId  |
| * &#128270; &#11016; | job| objectId  |
| * &#11016; | tax| objectId  |
| * | termCondition| string  |
| * &#128270; &#11016; | quotationJob| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | quickbookInvoiceId| string  |
|  | date| date  |
|  | discount| object  |
| * | discount.type| string  |
| * | discount.amount| string  |
| * | discount.description| string  |
| * | discount.totalDiscount| object  |
|  | discount.isShowPercentage| Boolean  |
|  | finalTotal| object  |
|  | note| string  |
|  | subTotal| object  |
|  | taxDetail| object  |
| * | taxDetail.number| string  |
| * | taxDetail.name| string  |
| * | taxDetail.rate| int  |
| * | taxDetail.totalTax| object  |
| &#11016; | updatedBy| objectId  |
|  | approvedDate| date  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |
|  | isRevised| Boolean  |
|  | isHoldback| Boolean  |
|  | isHoldbackApplied| Boolean  |
|  | holdbackAmount| object  |
|  | subTotalAfterHoldback| object  |
|  | reminderDate| date  |
|  | reminderSent| Boolean  |
|  | directInvoice| Boolean  |
|  | workOrderList| object  |
| * | workOrderList.technician| array  |
| * | workOrderList.materials| array  |
| &#128270; &#11016; | service| objectId  |
| &#128270; &#11016; | workOrder| objectId  |
|  | pdfKey| string  |
|  | depositAmount| object  |
|  | depositPercent| object  |
|  | clientName| string  |
|  | signature| string  |
|  | revisedDate| date  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | type\_1 | ON type|
| &#128270;  | quotationJob\_1 | ON quotationJob|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | client\_1 | ON client|
| &#128270;  | invoiceId\_1 | ON invoiceId|
| &#128270;  | company\_1 | ON company|
| &#128270;  | job\_1 | ON job|
| &#128270;  | service\_1 | ON service|
| &#128270;  | workOrder\_1 | ON workOrder|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( client ) ref [dev-jt.clients](#clients) (\_id) |
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( job ) ref [dev-jt.jobs](#jobs) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( service ) ref [dev-jt.services](#services) (\_id) |
| Vir | Relationship | ( tax ) ref [dev-jt.taxes](#taxes) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( workOrder ) ref [dev-jt.workorders](#workorders) (\_id) |




### Collection dev-jt.jobcostcategories 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | name| string  |
| * &#128270; &#11016; | company| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | addedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.jobcosts 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | label| string  |
| &#11016; | quotationJob| objectId  |
| * &#128270; &#11016; | category| objectId  |
| * | date| date  |
|  | description| string  |
|  | vendor| string  |
| * | cost| object  |
| * | unit| string  |
| * | quantity| object  |
| * | taxDetail| object  |
|  | taxDetail.number| string  |
| * | taxDetail.name| string  |
| * | taxDetail.rate| object  |
| * | taxDetail.totalTax| object  |
|  | receipt| string  |
| * | totalCost| object  |
| * &#128270; &#11016; | company| objectId  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | updatedBy| objectId  |
|  | fileExtension| string  |
|  | fileName| string  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |
|  | quickbookJobCostId| string  |
| &#128270; &#11016; | timesheetEntry| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | category\_1 | ON category|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | timesheetEntry\_1 | ON timesheetEntry|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( category ) ref [dev-jt.jobcostcategories](#jobcostcategories) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( timesheetEntry ) ref [dev-jt.timesheetentries](#timesheetentries) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.jobs 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | name| string  |
| * | address| object  |
| * | address.location| string  |
| * | address.street| string  |
| * | address.unit| string  |
| * | address.city| string  |
| * | address.state| string  |
| * | address.pincode| string  |
| * &#128270; &#11016; | company| objectId  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | updatedBy| objectId  |
|  | purchaseOrder| string  |
|  | contract| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.lineitems 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | name| string  |
|  | description| string  |
|  | amount| object  |
| * &#128270; &#11016; | company| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | \_\_v| int  |
| * | createdAt| date  |
| * | updatedAt| date  |
| &#11016; | updatedBy| objectId  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |
|  | subLineItems| array[object]  |
| * | subLineItems.label| string  |
| * | subLineItems.description| string  |
| * | subLineItems.amount| int  |
| * | subLineItems.isInvoiceFull| Boolean  |
| * | subLineItems.discount| object  |
| * | subLineItems.discount.type| string  |
| * | subLineItems.discount.amount| string  |
| * | subLineItems.discount.description| string  |
| * | subLineItems.discount.totalDiscount| int  |
| * | subLineItems.finalAmount| int  |
| * | subLineItems.subSubLineItems| array[object]  |
| * | subLineItems.subSubLineItems.label| string  |
| * | subLineItems.subSubLineItems.amount| int  |
| * | subLineItems.subSubLineItems.type| string  |
| * | subLineItems.subSubLineItems.quantity| int  |
| * | subLineItems.subSubLineItems.totalAmount| int  |
| * | subLineItems.subSubLineItems.\_id| objectId  |
|  | subLineItems.subSubLineItems.markup| int  |
| * | subLineItems.\_id| objectId  |
|  | addedBy| objectId  |
|  | markup| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.logs 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | action| string  |
| * | title| string  |
| * &#11016; | company| objectId  |
| * &#128270; &#11016; | user| objectId  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#128270; | timesheet| string  |
|  | timesheetEntry| string  |
|  | quickbooksynced| Boolean  |
|  | withoutSend| Boolean  |
| &#11016; | job| objectId  |
| &#11016; | invoice| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | user\_1 | ON user|
| &#128270;  | timesheetEntry\_1 | ON timesheet|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( invoice ) ref [dev-jt.invoices](#invoices) (\_id) |
| Vir | Relationship | ( job ) ref [dev-jt.jobs](#jobs) (\_id) |
| Vir | Relationship | ( user ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.notes 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | title| string  |
| * | note| string  |
|  | color| string  |
| &#11016; | quotationJob| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |
| &#11016; | updatedBy| objectId  |
| &#128270; &#11016; | workOrder| objectId  |
| &#11016; | client| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | workOrder\_1 | ON workOrder|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( client ) ref [dev-jt.clients](#clients) (\_id) |
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( workOrder ) ref [dev-jt.workorders](#workorders) (\_id) |




### Collection dev-jt.notesettings 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | note| string  |
| * &#128270; | type| string  |
| * &#128270; &#11016; | company| objectId  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | paymentDue| object  |
| * | paymentDue.days| int  |
| &#11016; | updatedBy| objectId  |
|  | serialNumber| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | type\_1 | ON type|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.notifications 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | title| string  |
| * | type| string  |
| * | action| string  |
| * &#11016; | receiver| array[objectid]  |
| &#11016; | quotationJob| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * &#128270; | isDeleted| Boolean  |
|  | readBy| array[object]  |
| * | readBy.user| objectId  |
| * | readBy.\_id| objectId  |
| * | readBy.readAt| date  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#128270; &#11016; | invoice| objectId  |
| &#128270; | workOrder| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | workOrder\_1 | ON workOrder|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | invoicePayment\_1 | ON invoice|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( invoice ) ref [dev-jt.invoices](#invoices) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( receiver ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.payments 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | invoice| string  |
| * | amountDue| object  |
| * | amountPaid| object  |
| * | charge| string  |
| * | collectionMethod| string  |
| * | customer| string  |
| * | customerEmail| string  |
| * | customerName| string  |
| * | invoicePDf| string  |
| * | number| string  |
| * | isPaid| Boolean  |
| * | status| string  |
| &#11016; | company| objectId  |
| &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | subscription| objectId  |
|  | paymentIntent| string  |
|  | paymentMethod| string  |
|  | subscriptionId| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( subscription ) ref [dev-jt.subscriptions](#subscriptions) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.pdfsettings 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | logo| string  |
| * | logoKey| string  |
|  | color| string  |
| * &#128270; | type| string  |
| * &#128270; &#11016; | company| objectId  |
| * | isActive| Boolean  |
|  | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | updatedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | type\_1 | ON type|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |




### Collection dev-jt.promocodes 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | promo\_code| string  |
| * | promo\_description| string  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|



### Collection dev-jt.quotationjobs 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | status| string  |
| * &#11016; | client| objectId  |
| * &#128270; &#11016; | job| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | jobId| string  |
| * | \_\_v| int  |
|  | archiveEmailSent| Boolean  |
|  | reminderSent| Boolean  |
| &#11016; | deletedBy| objectId  |
|  | reminderDate| date  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | jobId\_1 | ON job|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( client ) ref [dev-jt.clients](#clients) (\_id) |
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( job ) ref [dev-jt.jobs](#jobs) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.recurringevents 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * &#128270; &#11016; | event| objectId  |
| * | recurrenceType| string  |
| * | endType| string  |
|  | endDate| date  |
| * | occurrences| int  |
| * | skipDates| array  |
| * | customDates| array  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | event\_1 | ON event|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( event ) ref [dev-jt.events](#events) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.referfriends 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | name| string  |
| * &#128270; | email| string  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | email\_1 | ON email|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.sequences 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| object  |
| * &#128269; | seq| int  |
| * | \_\_v| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128269;  | \_id\_1\_seq\_1 | ON \_id, seq|



### Collection dev-jt.services 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | serviceLabel| string  |
| * | callerName| string  |
| * | address| object  |
|  | address.location| string  |
| * | address.street| string  |
| * | address.city| string  |
| * | address.state| string  |
| * | address.pincode| string  |
|  | address.unit| string  |
| * &#128270; &#11016; | company| objectId  |
| * | siteContactNumber| string  |
| * | siteContactName| string  |
| * | client| string  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | updatedBy| objectId  |
|  | purchaseOrder| string  |
|  | contract| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.slackchannels 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * &#128270; | channelId| string  |
| * | \_\_v| int  |
| * | createdAt| date  |
| * &#128270; | isActive| Boolean  |
| * &#128270; | isDeleted| Boolean  |
| * | isPrivate| Boolean  |
| * | name| string  |
| * | updatedAt| date  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | channelId\_1 | ON channelId|
| &#128270;  | isActive\_1 | ON isActive|



### Collection dev-jt.slackevents 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | value| string  |
| * | \_\_v| int  |
| * | createdAt| date  |
| * &#128270; | isActive| Boolean  |
| * &#128270; | isDeleted| Boolean  |
| * | name| string  |
| * | updatedAt| date  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isActive\_1 | ON isActive|
| &#128270;  | isDeleted\_1 | ON isDeleted|



### Collection dev-jt.slacknotifications 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | title| string  |
| * &#11016; | slackEvent| objectId  |
| * &#11016; | slackChannel| objectId  |
| * &#128270; | isActive| Boolean  |
| * | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| * | updatedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | isActive\_1 | ON isActive|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( slackChannel ) ref [dev-jt.slackchannels](#slackchannels) (\_id) |
| Vir | Relationship | ( slackEvent ) ref [dev-jt.slackevents](#slackevents) (\_id) |




### Collection dev-jt.subscriptionplans 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | name| string  |
| * | \_\_v| int  |
| * | benefits| array[string]  |
| * | createdAt| date  |
| * | description| string  |
| * | duration| int  |
| * &#128270; | isDeleted| Boolean  |
| * | price| int  |
| * | type| string  |
| * | updatedAt| date  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|



### Collection dev-jt.subscriptions 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | subscriptionId| string  |
| * | collectionMethod| string  |
| * | currentperiodEnd| date  |
| * | currentperiodStart| date  |
| * | customer| string  |
| * | plan| string  |
| * | amount| int  |
| * | product| string  |
| * | status| string  |
| * | defaultPaymentMethod| string  |
| * | subscriptionPlan| string  |
| * &#11016; | company| objectId  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.syncemaildetails 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * &#128270; &#11016; | user| objectId  |
| * | type| string  |
| * &#128270; | email| string  |
| * | appPassword| string  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | user\_1 | ON user|
| &#128270;  | email\_1 | ON email|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( user ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.tasks 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | name| string  |
| * | note| string  |
| * | priority| int  |
| * &#128270; | isCompleted| Boolean  |
| * &#128270; &#11016; | quotationJob| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | updatedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | isCompleted\_1 | ON isCompleted|
| &#128270;  | quotationJob\_1 | ON quotationJob|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( quotationJob ) ref [dev-jt.quotationjobs](#quotationjobs) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.taxes 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * | number| object  |
| * | name| string  |
| * | rate| object  |
| * | isDefault| Boolean  |
| * &#128270; &#11016; | company| objectId  |
| &#11016; | addedBy| objectId  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#11016; | updatedBy| objectId  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.templates 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * | action| string  |
| * &#128270; &#11016; | company| objectId  |
| * | \_\_v| int  |
| * | createdAt| date  |
| * | description| string  |
|  | followUp| array[object]  |
| * | followUp.days| int  |
| * | followUp.time| string  |
| * | followUp.date| date  |
| * | followUp.subject| string  |
| * | followUp.template| string  |
| * | isActive| Boolean  |
| * &#128270; | isDeleted| Boolean  |
| * | title| string  |
| * | type| string  |
| * | updatedAt| date  |
|  | updatedBy| objectId  |
|  | subject| string  |
|  | template| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |




### Collection dev-jt.timesheetentries 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * &#128270; &#11016; | job| objectId  |
| * &#128270; &#11016; | timesheet| objectId  |
| &#128270; | checkIn| date  |
|  | status| string  |
| * &#128270; | isDeleted| Boolean  |
|  | checkInLatLong| array[double]  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
| &#128270; | checkOut| date  |
|  | notes| array[string]  |
|  | totalTimeHours| int  |
|  | totalTimeMinutes| int  |
| &#128270; | manual| Boolean  |
| &#128270; | isTravelTime| Boolean  |
| &#11016; | approver| objectId  |
| &#11016; | rejectedBy| objectId  |
|  | title| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | job\_1 | ON job|
| &#128270;  | timesheet\_1 | ON timesheet|
| &#128270;  | checkInLatLong\_2d | ON checkIn|
| &#128270;  | checkOutLatLong\_2d | ON checkOut|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | manual\_1 | ON manual|
| &#128270;  | isTravelTime\_1 | ON isTravelTime|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( job ) ref [dev-jt.jobs](#jobs) (\_id) |
| Vir | Relationship | ( timesheet ) ref [dev-jt.timesheets](#timesheets) (\_id) |
| Vir | Relationship | ( approver ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( rejectedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.timesheets 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * &#11016; | user| objectId  |
| * | date| date  |
| * &#128270; &#11016; | company| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | totalTimeHours| int  |
| * | totalTimeMinutes| int  |
| * | \_\_v| int  |
| &#128270; | checkIn| date  |
| &#128270; | checkOutLatLong| array[double]  |
|  | checkOut| date  |
| &#11016; | deletedBy| objectId  |
| &#128270; | isReminderSent| Boolean  |
| &#128270; | manual| Boolean  |
|  | checkInLatLong| array[double]  |
|  | reason| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | checkInLatLong\_2d | ON checkIn|
| &#128270;  | checkOutLatLong\_2d | ON checkOutLatLong|
| &#128270;  | manual\_1 | ON manual|
| &#128270;  | isReminderSent\_1 | ON isReminderSent|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( user ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.user details 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( null ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( null ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.userdetails 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * &#128270; &#11016; | user| objectId  |
| * &#128270; &#11016; | company| objectId  |
| * &#128270; | type| string  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | status| string  |
|  | lm\_data| string  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | company\_1 | ON company|
| &#128270;  | type\_1 | ON type|
| &#128270;  | user\_1 | ON user|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( user ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.userpermissions 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  | \_id| objectId  |
| * &#128270; &#11016; | userId| objectId  |
| * | permissions| array[object]  |
| * | permissions.monetaryValues| Boolean  |
|  | permissions.jobs| object  |
| * | permissions.jobs.actions| array[string]  |
| * | permissions.quotation| object  |
| * | permissions.quotation.actions| array  |
| * | permissions.lineItems| object  |
| * | permissions.lineItems.actions| array[string]  |
| * | permissions.notes| object  |
| * | permissions.notes.actions| array[string]  |
| * | permissions.attachments| object  |
| * | permissions.attachments.actions| array[string]  |
| * | permissions.history| object  |
| * | permissions.history.monetaryValues| Boolean  |
| * | permissions.history.actions| array  |
| * | permissions.invoice| object  |
| * | permissions.invoice.actions| array  |
| * | permissions.workOrder| object  |
| * | permissions.workOrder.invoice| Boolean  |
| * | permissions.workOrder.actions| array[string]  |
| * | permissions.schedule| object  |
| * | permissions.schedule.own| Boolean  |
| * | permissions.schedule.actions| array[string]  |
| * | permissions.client| object  |
| * | permissions.client.actions| array  |
| * | permissions.\_id| objectId  |
|  | permissions.reports| Boolean  |
|  | permissions.timesheet| object  |
| * | permissions.timesheet.own| Boolean  |
| * | permissions.timesheet.actions| array[string]  |
| * | permissions.timesheet.everyone| Boolean  |
|  | permissions.jobCost| object  |
| * | permissions.jobCost.own| Boolean  |
| * | permissions.jobCost.actions| array  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | userId\_1 | ON userId|
| &#128270;  | isDeleted\_1 | ON isDeleted|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( userId ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.users 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * &#128269; | email| string  |
|  | password| string  |
|  | firstName| string  |
| * | identifier| string  |
| * | identifierConfirmed| Boolean  |
| * | isProfileCompleted| Boolean  |
| * &#128270; | isActive| Boolean  |
| * | role| string  |
| &#128270; &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * &#128269; | userId| int  |
| * | \_\_v| int  |
|  | ipAddress| string  |
| &#11016; | updatedBy| objectId  |
|  | identifierToken| string  |
|  | identifierTokenExpiry| date  |
|  | lastName| string  |
|  | homeScreenIcon| Boolean  |
|  | quickbook| object  |
|  | quickbook.syncedExpAt| date  |
|  | quickbook.realmId| string  |
| * | quickbook.refresh\_token| string  |
|  | timezone| string  |
|  | isBillingUpdate| Boolean  |
|  | isGoogleEmailSync| Boolean  |
|  | isOutLookSync| Boolean  |
|  | image| string  |
|  | imageKey| string  |
|  | stripeAccountId| string  |
|  | fcmToken| array  |
|  | leadId| string  |
|  | leadSource| string  |
|  | opportunityId| string  |
|  | accessType| string  |
|  | employeeType| string  |
|  | jobTitle| string  |
|  | rate| object  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | addedBy\_1 | ON addedBy|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128269;  | userId\_1 | ON userId|
| &#128269;  | email\_1 | ON email|
| &#128270;  | isActive\_1 | ON isActive|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |




### Collection dev-jt.workorders 
|Idx |Name |Data Type |
|---|---|---|
| * &#128273;  &#11019; | \_id| objectId  |
| * &#128270; | workOrderId| string  |
| * &#128270; | type| string  |
| * | workOrderList| object  |
|  | workOrderList.technician| array[object]  |
| * | workOrderList.technician.techLabel| string  |
| * | workOrderList.technician.timeIn| date  |
| * | workOrderList.technician.timeOut| date  |
| * | workOrderList.technician.workedHours| string  |
| * | workOrderList.technician.\_id| objectId  |
|  | workOrderList.technician.timeStringIn| string  |
|  | workOrderList.technician.timeStringOut| string  |
|  | workOrderList.materials| array[object]  |
| * | workOrderList.materials.materialLabel| string  |
| * | workOrderList.materials.quantity| int  |
| * | workOrderList.materials.\_id| objectId  |
|  | workOrderList.label| string  |
|  | workOrderList.description| string  |
|  | workOrderList.recommendations| string  |
| * | paymentDue| object  |
| * | paymentDue.reminderSent| Boolean  |
| * | reminderSent| Boolean  |
| * | reminder| object  |
| * | reminder.isSent| Boolean  |
| * | reminder.isSecondSent| Boolean  |
| * | status| string  |
| * &#128270; &#11016; | client| objectId  |
| * &#128270; &#11016; | service| objectId  |
| * | tax| string  |
| * | recommendations| string  |
| * &#128270; &#11016; | company| objectId  |
| * &#128270; | workOrderQuoteId| string  |
| * &#11016; | addedBy| objectId  |
| * &#128270; | isDeleted| Boolean  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | date| date  |
|  | note| string  |
|  | reminderDate| date  |
| &#11016; | updatedBy| objectId  |
|  | deletedAt| date  |
| &#11016; | deletedBy| objectId  |
|  | discount| object  |
| * | discount.type| string  |
| * | discount.amount| string  |
| * | discount.description| string  |
| * | discount.totalDiscount| int  |
| * | discount.isShowPercentage| Boolean  |
|  | pdfKey| string  |
|  | clientName| string  |
|  | clientSignature| string  |
|  | techName| string  |
|  | techSignature| string  |
|  | invoicedAt| date  |


##### Indexes 
|Type |Name |On |
|---|---|---|
| &#128273;  | \_id\_ | ON \_id|
| &#128270;  | client\_1 | ON client|
| &#128270;  | service\_1 | ON service|
| &#128270;  | company\_1 | ON company|
| &#128270;  | workOrderQuoteId\_1 | ON workOrderQuoteId|
| &#128270;  | isDeleted\_1 | ON isDeleted|
| &#128270;  | workOrderId\_1 | ON workOrderId|
| &#128270;  | type\_1 | ON type|

##### Relationships
|Type |Name |On |
|---|---|---|
| Vir | Relationship | ( client ) ref [dev-jt.clients](#clients) (\_id) |
| Vir | Relationship | ( company ) ref [dev-jt.companies](#companies) (\_id) |
| Vir | Relationship | ( service ) ref [dev-jt.services](#services) (\_id) |
| Vir | Relationship | ( addedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( updatedBy ) ref [dev-jt.users](#users) (\_id) |
| Vir | Relationship | ( deletedBy ) ref [dev-jt.users](#users) (\_id) |





## View user details

Query user details
```

```

|Idx |Name |Type |
|---|---|---|
| * | \_id| objectId  |
|  | company| object  |
| * | company.\_id| objectId  |
|  | company.name| string  |
| * | company.image| string  |
| * | company.subscription| object  |
| * | company.subscription.validTo| date  |
| * | company.subscription.status| string  |
| * | company.subscription.validFrom| date  |
|  | company.subscription.activeDate| date  |
|  | company.subscription.updatedAt| date  |
|  | company.subscription.cancelledDate| date  |
|  | company.subscription.extendDate| date  |
| * | company.createdAt| date  |
| * | company.updatedAt| date  |
| * | company.\_\_v| int  |
| * | company.userDetail| objectId  |
| * | company.stripe| object  |
| * | company.stripe.customer| string  |
|  | company.stripe.subscription| string  |
|  | company.imageKey| string  |
|  | company.address| object  |
|  | company.address.location| string  |
|  | company.address.street| string  |
|  | company.address.unit| string  |
|  | company.address.city| string  |
|  | company.address.state| string  |
|  | company.address.country| string  |
|  | company.address.pincode| string  |
|  | company.phoneNumber| string  |
|  | company.website| string  |
|  | company.isDisabled| Boolean  |
| * | type| string  |
| * | createdAt| date  |
| * | updatedAt| date  |
| * | \_\_v| int  |
|  | user| object  |
| * | user.\_id| objectId  |
| * | user.email| string  |
|  | user.password| string  |
|  | user.firstName| string  |
| * | user.identifier| string  |
| * | user.identifierConfirmed| Boolean  |
| * | user.isProfileCompleted| Boolean  |
| * | user.isActive| Boolean  |
| * | user.role| string  |
|  | user.addedBy| objectId  |
| * | user.isDeleted| Boolean  |
| * | user.createdAt| date  |
| * | user.updatedAt| date  |
| * | user.userId| int  |
| * | user.\_\_v| int  |
|  | user.ipAddress| string  |
|  | user.updatedBy| objectId  |
|  | user.identifierToken| string  |
|  | user.identifierTokenExpiry| date  |
|  | user.lastName| string  |
|  | user.homeScreenIcon| Boolean  |
|  | user.quickbook| object  |
| * | user.quickbook.syncedExpAt| date  |
| * | user.quickbook.realmId| string  |
| * | user.quickbook.refresh\_token| string  |
|  | user.timezone| string  |
|  | user.isBillingUpdate| Boolean  |
|  | user.isGoogleEmailSync| Boolean  |
|  | user.isOutLookSync| Boolean  |
|  | user.fcmToken| array  |
|  | user.jobTitle| string  |
|  | user.accessType| string  |
|  | user.rate| int  |
|  | user.employeeType| string  |
|  | user.leadSource| string  |
|  | status| string  |
|  | lm\_data| string  |

