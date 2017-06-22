1. **両方のクラスター ノードで、Pacemaker にログインするための SQL Server のユーザー名とパスワードを格納するファイルを作成します**。 次のコマンドは、このファイルを作成および設定します。

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd
    ```
2. **すべてのクラスター ノードは、SSH を使用して相互にアクセスできる必要があります**。 hb_report or crm_report (トラブルシューティング用) などのツールや Hawk の History Explorer では、ノード間でパスワードなしの SSH アクセスが必要です。それ以外の場合は、現在のノード以外のデータは収集できません。 非標準の SSH ポートを使用する場合は、-X オプションを使用します (man ページを参照)。 たとえば、SSH ポートが 3479 の場合は、次のコマンドを実行して hb_report を呼び出します。

    ```bash
    crm_report -X "-p 3479" [...]
    ```

    詳細については、[SUSE ドキュメントのシステム要件と推奨事項](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html)をご覧ください。

3. **High Availability Extension をインストールします**。 High Availability Extension をインストールするには、次の SUSE のトピックの手順を実行します。
    
    [インストールとセットアップのクイック スタート](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html)

4. **SQL Server の FCI リソース エージェントをインストールします**。 両方のノードで、次のコマンドを実行します。

    ```bash
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server.repo
    sudo zypper --gpg-auto-import-keys refresh
    sudo zypper install mssql-server-ha
    ```

5. **最初のノードが自動的にセットアップされます**。 次の手順では、最初のノードである SLES1 を構成することにより、動作中の 1 ノード クラスターをセットアップします。 SUSE のトピック「[Setting Up the First Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node) (最初のノードのセットアップ)」の指示に従ってください。

    完了したら、`crm status` を使用してクラスターの状態を確認します。
    ```bash
    crm status
    ```

    ノード SLES1 が構成済みであることが表示されます。

6. **既存のクラスターにノードを追加します**。 次に、ノード SLES2 をクラスターに参加させます。 SUSE のトピック「[Adding the Second Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.2nd-node) (2 番目のノードの追加)」の指示に従います。
    
    完了したら、**crm status** を使用してクラスターの状態を確認します。 2 番目のノードが正常に追加されると、次のような出力が表示されます。
        
    ```
    2 nodes configured
    1 resource configured
    Online: [ SLES1 SLES2 ]
    Full list of resources:
    admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
    ```

    > [!NOTE]
    > **admin_addr** は、最初の 1 ノード クラスターのセットアップ時に構成された仮想 IP クラスターのリソースです。

7.  **削除手順**。 クラスターからノードを削除する必要がある場合は、ブートストラップ スクリプト **ha-cluster-remove** を使用します。 詳細については、「[Overview of the Bootstrap Scripts](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.bootstrap) (ブートストラップ スクリプトの概要)」をご覧ください。  

