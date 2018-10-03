1. **すべての SQL Server で、Pacemaker 用サーバー ログインを作成します**。 次の Transact-SQL がログインを作成します。

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

  可用性グループの作成時に、作成後、すべてのノードが追加される前に、pacemaker のユーザーにより、可用性グループで、ALTER、CONTROL、および VIEW DEFINITION アクセス許可が必要です。

1. **すべての SQL Server に、SQL Server ログインの資格情報を保存します**。

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
