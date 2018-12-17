# Advanced-Attachment-Copy-Util-Scripts
Script Includes to copy a specific attachment from one record to another &amp; to make a copy of a specific record. (update set xml also available)



Call copySpecificAttachment function to copy a specific attachment from one record to another. 
copySpecificAttachment takes the following arguments: 
1. Donor table. This is the name of the table that the donor record (the record FROM which attachments should be copied) resides in. 
2. Donor ID. This is the sys_id of the record from which the attachment should be copied. 
3. Recipient Table. This is the name of the table that the recipient record resides in. 
4. Recipient ID. This is the sys_id of the record to which the newly copied attachment should be associated. 
5. File name. This is the exact name of the attachment file to be copied, including the extension. (Ex: "quarterly_report.xlsx")


Call copyRecord function to make a copy of a specific record. 
This function takes one input: A GlideElement object, containing the record to be copied. 
copyRecord will make an EXACT copy of the record that is passed into it, except it will not copy the sys_id, or 'number' (if it exists). 
This function will also return a GlideRecord object containing the new record, so you can make any additional changes you'd like and then call .update() to save them. 
If you do not wish to make any additional changes to the newly copied record, it is not necessary to run .update(). 

Example usage: 
var newRecord = copyRecord(gr);
newRecord.setValue('short_description', 'This record was made as a copy of ' + gr.getValue('number') + '.');
newRecord.update();
