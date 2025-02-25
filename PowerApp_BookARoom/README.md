# Book-a-Room-with-powerapp

I am using an existing Powerapp Template "Book a Room" and modify there.
![image](https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/5389aad4-c735-4b29-a452-dfd62e86b61d)


## Modification I had made
![image](https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/c3b94700-4b25-4f1c-a218-76737aa80b3b)

### 1. Filter your search Room auto selected by your Account location country at search object 
>Default - First(Office365Users.SearchUser({searchTerm:User().Email}).Country).Country

this will filter your room list based on your country location.
<img width="628" alt="image" src="https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/c118c2b9-47a3-4823-8e14-2ebf2465e22a">

### 2. to show the capacity of a room
-upon my reasearch there is no function available in powerapp to display room capacity. this is a workaround solution with SharePoint.
![image](https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/866abe9b-4000-4418-bb0f-c3a485c89f9b)

### 2.1. Create a SharePoint name "RoomList" as follows
The title room name must be the exact same name as your meeting room mailbox that was created in your exchange.
<img width="480" alt="image" src="https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/1c3d799d-1508-4f85-a296-ba85dce07b12">

### 2.2. Add a new "text label" to the "RoomGallery"
> add this to read the data from RoomList SharePoint
>  - "Size-" & First(Filter(RoomList, Title = ThisItem.Name)).Capacity
![image](https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/12b69627-62e4-4bf4-916a-604b37d06cc7)

### 3. Popup box for booking confirmation
created the following popup object under the "RoomSelectScreen
![image](https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/5836910b-288c-4ecb-967a-0e6a375742a0)

- Label_date
> Text - "Date: " & Text(DateSelected, "[$-en-US]mmmm dd, yyyy")

- Label_time
> Text - "Time: " & Text(StartDateTime, DateTimeFormat.ShortTime) & " - " & Text(EndDateTime, DateTimeFormat.ShortTime)

- Label-popupConfirm
> Text - "You have selected"

- btn_Confirm 
> OnSelect - Set(IsBooking, true);  Navigate(ConfirmationScreen, ScreenTransition.Cover); UpdateContext ({varDisplayPopup:false})

- btn_Cancel 
> Onselect - UpdateContext ({varDisplayPopup:false})

Group them together and set visible value to 
> varDisplayPopup
![image](https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/4b5d797f-88be-49cb-a124-e2b154c9baeb)


### 4. Cancel a meeting
- create cancel button
> Onselect - Office365.CalendarDeleteItemV2(MyCalendar,ThisItem.Id);Remove(FutureCalendarEvents,ThisItem);
![image](https://github.com/SGA-JS/Book-a-Room-with-PowerApp/assets/73696641/c3d8bcb1-4fe1-493c-9b46-2c9148083aed)







  
