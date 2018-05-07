---
title: 'フェールオーバー クラスター インスタンス記憶域 iSCSI: Linux 上の SQL Server の構成 |Microsoft ドキュメント'
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.openlocfilehash: 514d19e4358b536109c76112115bac380f390bce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configure-failover-cluster-instance---iscsi---sql-server-on-linux"></a>フェールオーバー クラスター インスタンス - iSCSI: Linux 上の SQL Server を構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上のフェールオーバー クラスター インスタンス (FCI) の iSCSI 記憶域を構成する方法について説明します。 

## <a name="configure-iscsi"></a>ISCSI を構成します。 
iSCSI では、ネットワークを使用して、サーバーをターゲットと呼ばれるサーバーからディスクを提示します。 ISCSI ターゲットに接続しているサーバーでは、iSCSI イニシエーターが構成されていることが必要です。 これにアクセスできる必要があります、イニシエーターのみを行うように、ターゲット上のディスクには明示的なアクセス許可が与えられます。 ターゲット自体は、高可用性と信頼性の高いにする必要があります。

### <a name="important-iscsi-target-information"></a>重要な iSCSI ターゲットの情報
このセクションを使用するソースの種類に固有であるため、iSCSI ターゲットを構成する方法については説明は、間には、クラスター ノードで使用されるディスクのセキュリティが構成されていることを確認します。  

ターゲットは Linux ベースの iSCSI ターゲットを使用する場合、FCI のノードのいずれで構成する必要があることはありません。 パフォーマンスと可用性は、iSCSI ネットワークは、ソースと、クライアント サーバーの両方で正規のネットワーク トラフィックで使用されるものとは別にする必要があります。 ISCSI に使用するネットワークは、高速にする必要があります。 そのネットワークはいくつかのプロセッサの帯域幅の使用、適切に計画、定期的なサーバーを使用する場合に注意してください。
確認する最も重要な点は、作成されたディスクが割り当てられている適切なアクセス許可、FCI に参加しているサーバーのみがそれらにアクセスできるようには、ターゲット上で完了します。 例は、Microsoft iSCSI ターゲット linuxnodes1 が作成されると、名前、NewFCIDisk1.vhdx がそれらに表示されるようにここでは、ノードの IP アドレスが割り当てられてから以下に示します。

![Initiator][1]

### <a name="instructions"></a>Instructions

このセクションでは、FCI のノードとして使用するサーバー上の iSCSI イニシエーターを構成する方法について説明します。 手順は RHEL および Ubuntu では、動作します。

サポートされている分布の iSCSI イニシエーターの詳細については、次のリンクを参照してください。
- [Red Hat](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/iscsi-api.html)
- [SUSE](http://www.suse.com/documentation/sles11/stor_admin/data/sec_inst_system_iscsi_initiator.html) 
- [Ubuntu](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

1.  FCI の構成では、参加するサーバーのいずれかを選択します。 どちらかは関係ありません。 iSCSI にする必要があります、専用のネットワーク上を認識し、そのネットワークを使用して iSCSI を構成するためです。 実行`sudo iscsiadm -m iface -I <iSCSIIfaceName> -o new`場所`<iSCSIIfaceName>`ネットワークに一意であるか、またはわかりやすい名前を指定します。 `iSCSINIC` の使用例を次に示します。
   
    ```bash
    sudo iscsiadm -m iface -I iSCSINIC -o new
    ```
    ![7 setiscsinetwork][6]
 
2.  編集`/var/lib/iscsi/ifaces/iSCSIIfaceName`です。 完全に記入する次の値があることを確認します。

    - iface.net_ifacename は、OS で表示されるネットワーク カードの名前です。
    - iface.hwaddress は、このインターフェイスの下に作成される一意の名前の MAC アドレスです。
    - iface.ipaddress
    - iface.subnet_Mask 

    次の例を参照してください。

    ![iSCSITargetSettings][2]

3.  ISCSI ターゲットを検索します。

    ```bash
    sudo iscsiadm -m discovery -t sendtargets -I <iSCSINetName> -p <TargetIPAddress>:<TargetPort>
    ```

     \<iSCSINetName >、ネットワークの一意な/フレンドリ名は、 \<TargetIPAddress > は、iSCSI ターゲットの IP アドレスと\<TargetPort > iSCSI ターゲットのポートです。 

    ![iSCSITargetResults][3]

 
4.  ターゲットにログインします。

    ```bash
    sudo iscsiadm -m node -I <iSCSIIfaceName> -p TargetIPAddress -l
    ```

    \<iSCSIIfaceName > ネットワークの一意な/フレンドリ名と\<TargetIPAddress > は、iSCSI ターゲットの IP アドレスです。

    ![iSCSITargetLogin][4]

5.  ISCSI ターゲットへの接続があることを確認します。

    ```bash
    sudo iscsiadm -m session
    ```

    ![iSCSIVerify][5]

 
6.  ISCSI 接続ディスクをチェックします。

    ```bash
    sudo grep “Attached SCSI” /var/log/messages
    ```
    ![30-iSCSIattachedDisks][7]

7.  ISCSI ディスク上の物理ボリュームを作成します。

    ```bash
    sudo pvcreate /dev/<devicename>
    ```

    \<devicename > 前の手順でデバイスの名前を指定します。 

 
8.  ISCSI ディスク上のボリューム グループを作成します。 1 つのボリューム グループに割り当てられているディスクは、プールまたはコレクションと見なされます。 

    ```bash
    sudo vgcreate <VolumeGroupName> /dev/devicename
    ```

    \<VolumeGroupName > ボリューム グループの名前を指定し、 \<devicename > 手順 6. からデバイスの名前を指定します。 
 
9.  作成し、論理ディスクのボリュームのことを確認します。

    ```bash
    sudo lvcreate -Lsize -n <LogicalVolumeName> <VolumeGroupName>
    ```
    
    \<サイズ > を作成するボリュームのサイズは、G (ギガバイト単位)、T (テラバイト) などを指定できます\<LogicalVolumeName > 論理のボリュームの名前を指定し、 \<VolumeGroupName > からボリューム グループの名前を指定します、前の手順です。 

    次の例では、25 GB のボリュームを作成します。
 
    ![Create25GBVol][10]

10. 実行`sudo lvs`に作成された LVM を参照してください。
 
11. サポートされているファイル システムで論理ボリュームをフォーマットします。 EXT4、次の例を使用します。

    ```bash
    sudo mkfs.ext4 /dev/<VolumeGroupName>/<LogicalVolumeName>
    ```

    \<VolumeGroupName > 前の手順からボリューム グループの名前を指定します。 \<LogicalVolumeName > 前の手順の論理ボリュームの名前を指定します。  

12. システム データベースまたはデータの既定の場所に格納されているものは、次の手順に従います。 それ以外の場合、手順 13 に進みます。

   *    作業しているサーバーで SQL Server が停止していることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    スーパー ユーザーを完全にスイッチです。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    sudo -i
    ```

   *    Mssql ユーザーであることに切り替えます。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    su mssql
    ```

   *    SQL Server のデータを格納するファイルとログ ファイルを一時ディレクトリを作成します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > フォルダーの名前を指定します。 次の例では、/var/opt/mssql/TempDir をという名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/TempDir
    ```
    
   *    SQL Server データとログ ファイルを一時ディレクトリにコピーします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > 前の手順で、フォルダーの名前を指定します。
    
   *    ファイルがディレクトリであることを確認します。

    ```bash
    ls \<TempDir>
    ```
    \<TempDir > 手順 d からフォルダーの名前を指定します。

   *    既存の SQL Server データ ディレクトリからファイルを削除します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   *    ファイルが削除されたことを確認します。 次の図は、h を通じて c からシーケンス全体の例を示します。

    ```bash
    ls /var/opt/mssql/data
    ```

    ![45-CopyMove][8]
 
   *    型`exit`root ユーザーに戻る。

   *    SQL Server データ フォルダー内の iSCSI の論理ボリュームをマウントします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> /var/opt/mssql/data
    ``` 

    \<VolumeGroupName > ボリューム グループの名前を指定し、 \<LogicalVolumeName > が作成された論理ボリュームの名前を指定します。 次の構文の例では、前のコマンドからの論理ボリュームとボリューム グループと一致します。

    ```bash
    mount /dev/FCIDataVG1/FCIDataLV1 /var/opt/mssql/data
    ``` 

   *    Mssql をマウントの所有者を変更します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    chown mssql /var/opt/mssql/data
    ```

   *    Mssql をマウントのグループの所有権を変更します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    chgrp mssql /var/opt/mssql/data
    ``` 

   *    Mssql ユーザーに切り替えます。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    su mssql
    ``` 

   *    一時ディレクトリ/var/opt/mssql/data からファイルをコピーします。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    cp /var/opt/mssql/TempDir/* /var/opt/mssql/data
    ``` 

   *    ファイルがあることを確認します。

    ```bash
    ls /var/opt/mssql/data
    ``` 
 
   *    入力`exit`mssql 設定されません。
    
   *    入力`exit`ルート設定されません。

   *    SQL Server を起動します。 すべてが正しくコピーされた、セキュリティが適用されて正しく、SQL Server が表示されますを起動する場合は。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ``` 
 
   *    SQL Server を停止し、シャット ダウンがあることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ``` 

13. ユーザー データベースや、バックアップなどのシステム データベース以外のものを以下の手順を実行します。 既定の場所を使用して、だけの場合は、手順 14 をスキップします。

   *    スーパー ユーザーにするスイッチです。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    sudo -i
    ```

   *    SQL Server で使用されるフォルダーを作成します。 

    ```bash
    mkdir <FolderName>
    ```

    \<フォルダー名 > フォルダーの名前を指定します。 フォルダーの完全なパスを指定する必要があります、適切な場所ではない場合。 次の例では、/var/opt/mssql/userdata をという名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    前の手順で作成したフォルダーに、iSCSI の論理ボリュームをマウントします。 ユーザーは受け取りません受信正常終了した場合。
    
    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > ボリューム グループの名前を指定\<LogicalVolumeName >、作成した論理ボリュームの名前を指定し、 \<FolderName > フォルダーの名前を指定します。 構文の例は、以下に示します。

    ```bash
    mount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

   *    Mssql を作成したフォルダーの所有権を変更します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    chown mssql <FolderName>
    ```

    \<フォルダー名 > が作成されたフォルダーの名前を指定します。 例を次に示します。

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```
  
   *    Mssql を作成したフォルダーのグループを変更します。 ユーザーは受け取りません受信正常終了した場合。

    ```bash
    chown mssql <FolderName>
    ```

    \<フォルダー名 > が作成されたフォルダーの名前を指定します。 例を次に示します。

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```

   *    型`exit`スーパー ユーザーを設定できません。

   *    テストするには、そのフォルダーにデータベースを作成します。 次に示す例では、sqlcmd を使用してデータベースを作成、コンテキストを切り替える、ファイルが、OS レベルが存在し、一時的な場所を削除します。 SSMS を使用することができます。
  
    ![50 ExampleCreateSSMS][9]

   *    共有のマウントを解除します。 

    ```bash
    sudo umount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > ボリューム グループの名前を指定\<LogicalVolumeName >、作成した論理ボリュームの名前を指定し、 \<FolderName > フォルダーの名前を指定します。 構文の例は、以下に示します。

    ```bash
    sudo umount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

14. その唯一のペースには、ボリューム グループがアクティブ化することができますので、サーバーを構成します。

    ```bash
    sudo lvmconf --enable-halvm --services –startstopservices
    ```
 
15. サーバー上のボリューム グループの一覧を生成します。 何も表示されている iSCSI ディスクではないが、システムで使用されるように OS ディスクの。

    ```bash
    sudo vgs
    ```

16. ファイル/etc/lvm/lvm.conf のアクティブ化構成セクションを変更します。 次の行を構成します。

    ```bash
    volume_list = [ <ListOfVGsNotUsedByPacemaker> ]
    ```

    \<ListOfVGsNotUsedByPacemaker > は、FCI では使用されません手順 20 の出力からボリューム グループの一覧を示します。 コンマを引用符で囲まれたを分けてそれぞれの 1 つずつを配置します。 例を次に示します。

    ![55-ListOfVGs][11]
 
 
17. Linux の開始時に、ファイル システムをマウントします。 ペースのみが iSCSI ディスクをマウントできることを確認するには、ルート ファイル システムのイメージを再構築します。 

    完了するまで時間がかかる次のコマンドを実行します。 メッセージが表示されますありません戻る正常終了した場合。

    ```bash
    sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r)
    ```

18. サーバーを再起動します。

19. FCI に参加する別のサーバーでは、手順 1 ~ 6 を実行します。 これは、SQL Server に、iSCSI ターゲットを提示します。 
 
20. サーバー上のボリューム グループの一覧を生成します。 これにより、先ほど作成したボリューム グループが表示されます。 

    ```bash
    sudo vgs
    ``` 
23. SQL Server を起動し、このサーバーで起動できることを確認します。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```

24. SQL Server を停止し、シャット ダウンすることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
25. FCI に参加する他のサーバーで手順 1 ~ 6 を繰り返します。

FCI を構成する準備が整いました。

|Distribution |トピック 
|----- |-----
|**HA アドオンで、Red Hat Enterprise Linux** |[構成します。](sql-server-linux-shared-disk-cluster-configure.md)<br/>[操作](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**HA アドオンに SUSE Linux Enterprise Server** |[構成します。](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>次の手順

[フェールオーバー クラスター インスタンス: Linux 上の SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/05-initiator.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/10-iscsiTargetSettings.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/15-iSCSITargetResults.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/20-iSCSITargetLogin.png
[5]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/25-iSCSIVerify.png
[6]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/7-setiscsinetwork.png
[7]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/30-iSCSIattachedDisks.png
[8]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/45-CopyMove.png
[9]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/50-ExampleCreateSSMS.png
[10]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/40-Create25GBVol.png
[11]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/55-ListOfVGs.png
