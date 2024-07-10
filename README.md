# Outlook Calendar: Display Who Booked the Room Instead of "Busy" / Outlook日曆：顯示誰預訂了房間而不是“忙碌”

In Outlook, by default, when a room is booked, the calendar shows the status as "Busy" without revealing who made the booking. 
在Outlook中，默認情況下，當房間被預訂時，日曆顯示狀態為“忙碌”，而不會顯示誰進行了預訂。

To change this behavior and display the name of the person who booked the room, follow these steps:
若要更改此行為並顯示預訂房間的人的姓名，請按照以下步驟操作：

1. **Connect to Exchange Online**:
   1. **連接到Exchange Online**：

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName Demo@contoso.com
   ```

2. **Get the Calendar Processing Settings for the Room**:
   2. **獲取房間的日曆處理設置**：

   ```powershell
   Get-CalendarProcessing -Identity "DemoRoom" | Format-List
   ```
***顯示配置訊息
   

3. **Set the Mailbox Folder Permission**:
   3. **設置郵箱文件夾權限**：

   To allow users to see limited details about the room bookings, use the following command:
   為了允許用戶查看房間預訂的有限詳細信息，請使用以下命令：

   ```powershell
   Set-MailboxFolderPermission -Identity DemoRoom:\calendar -User default -AccessRights LimitedDetails
   ```

By following these steps, the calendar will display the names of individuals who have booked the room instead of just showing "Busy".
通過按照這些步驟操作，日曆將顯示預訂房間的人的姓名，而不僅僅顯示“忙碌”。
