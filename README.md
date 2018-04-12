# Binder
Custom javascript tool for client-side input fields updating and commiting to server

## Usage
After document load, call function Binder(settings) , where settings is object containing default values. Settings object must contain object area, specifying html caller element containing one row.

 * Caller element should contain attributes data-binder-table and data-binder-id, specifying table name and id of record.
 * Caller element may contain save button, specified by its class (default binder-save-btn)
 * Caller element may contain delete button, specified by its class (default binder-delete-btn)
 * Caller element must contain database field elements, containing the data - INPUT, SELECT or TEXTAREA fields. Their name should correspond to its database field name. Each field element should also have attribute data-value containing original value, loaded from database.
 
 * Optional settings attribute is saveAllSelector, which can contain selector for specifying a button that saves all visible binder records.

 * Every element having attribute data-value is being treated as db field element. Whenever its changed, binder checks for all changes in the record (differences between the actual value and data-value attribute). If there is at least one change, binder changes the class of save button from btn-primary (btn-secondary etc. corresponding to Bootstrap v4 class names) to btn-outline-* to mark change saveable.
 * After clicking on save button, data with changed fields are sent via ajax to backend url. Url is taken from save button's href attribute. Object is having properties id, table and changes. Changes property contains key value pairs of changed items in records.
 * After succesfull save, save button class is reinstantized back to normal class.
 
 * After clicking on delete button, object, containing just id and table properties is sent to url, specified by delete button's href attribute. After succesfull ajax request, whole binder area gets deleted.
