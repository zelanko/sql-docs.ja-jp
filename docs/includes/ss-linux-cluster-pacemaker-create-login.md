1. **すべての SQL Server で、Pacemaker 用サーバー ログインを作成します**。 次の Transact-SQL がログインを作成します。

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
       
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

   または、より細かなレベルでアクセス許可を設定することもできます。 Pacemaker のログインには、ALTER、CONTROL、VIEW DEFINITION 権限が必要です。 詳細については、「[GRANT Availability Group Permissions (Transact-SQL)](http://msdn.microsoft.com/library/hh968934.aspx)(可用性グループの権限の許可 (Transact-SQL))」をご覧ください。

   次の Transact-SQL では、Pacemaker のログインに必要な権限のみを付与します。 "ag1" の下のステートメントは、クラスター リソースとして追加される可用性グループの名前です。

   ```Transact-SQL
   GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO pacemakerLogin
   ```

1. **すべての SQL Server に、SQL Server ログインの資格情報を保存します**。

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
