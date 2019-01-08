---
title: フェールオーバー クラスター インスタンス ストレージ iSCSI - SQL Server on Linux の構成 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: c73a91a461f78687d390e4ef620416325e7672df
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52524908"
---
# <a name="configure-failover-cluster-instance---iscsi---sql-server-on-linux"></a>フェールオーバー クラスター インスタンスの iSCSI - SQL Server on Linux を構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux でのフェールオーバー クラスター インスタンス (FCI) の iSCSI 記憶域を構成する方法について説明します。 

## <a name="configure-iscsi"></a>ISCSI を構成します。 
iSCSI では、ネットワークを使用して、サーバーをターゲットと呼ばれるサーバーからディスクを提示します。 ISCSI ターゲットに接続するサーバーでは、iSCSI イニシエーターが構成されていることが必要です。 ターゲット上のディスクは、それらにアクセスできるようにするイニシエーターのみがこれを実行できるように、明示的なアクセス許可が付与されます。 ターゲット自体には、高可用性と信頼性があります。

### <a name="important-iscsi-target-information"></a>重要な iSCSI ターゲットの情報
このセクションでは、使用するソースの種類に固有であるために、iSCSI ターゲットを構成する方法を説明していない、ときに、クラスター ノードで使用されるディスクのセキュリティが構成されていることを確認します。  

Linux ベースの iSCSI ターゲットを使用する場合、FCI ノードのいずれかでターゲットを構成しない必要があります。 パフォーマンスと可用性は、iSCSI ネットワークは、ソースと、クライアント サーバーの両方で通常のネットワーク トラフィックで使用されるものとは別にあります。 ISCSI に使用されるネットワークは、高速必要があります。 そのネットワークはいくつかのプロセッサ帯域幅を消費する、適切に計画正規サーバーを使用する場合に注意してください。
確認する最も重要な点は、FCI に参加しているサーバーのみがそれらにアクセスできるように、作成されるディスクに適切なアクセス許可を割り当てられては、ターゲット上で完了します。 例は、Microsoft iSCSI ターゲット linuxnodes1 が作成されると、名前、NewFCIDisk1.vhdx がそれらに表示されるように、ノードの IP アドレスが割り当てられているこの例では、以下に示します。

![Initiator][1]

### <a name="instructions"></a>Instructions

このセクションでは、FCI のノードとして機能するサーバーで iSCSI イニシエーターを構成する方法について説明します。 手順は、RHEL および Ubuntu 上に、機能する必要があります。

サポートされているディストリビューションの iSCSI イニシエーターの詳細については、次のリンクを参照してください。
- [Red Hat](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/iscsi-api.html)
- [SUSE](https://www.suse.com/documentation/sles11/stor_admin/data/sec_inst_system_iscsi_initiator.html) 
- [Ubuntu](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

1.  FCI の構成では、参加するサーバーのいずれかを選択します。 どれもかまいません。 iSCSI にする必要があります、専用のネットワークを認識し、そのネットワークを使用して、iSCSI を構成するようにします。 実行`sudo iscsiadm -m iface -I <iSCSIIfaceName> -o new`場所`<iSCSIIfaceName>`のネットワークまたは一意のわかりやすい名前を指定します。 `iSCSINIC` の使用例を次に示します。
   
    ```bash
    sudo iscsiadm -m iface -I iSCSINIC -o new
    ```
    ![7 setiscsinetwork][6]
 
2.  編集`/var/lib/iscsi/ifaces/iSCSIIfaceName`します。 完全に記入する次の値があることを確認します。

    - iface.net_ifacename は、OS に示すようにネットワーク カードの名前です。
    - iface.hwaddress は、このインターフェイスの下に作成される一意の名前の MAC アドレスです。
    - iface.ipaddress
    - iface.subnet_Mask 

    次の例を参照してください。

    ![iSCSITargetSettings][2]

3.  ISCSI ターゲットを検索します。

    ```bash
    sudo iscsiadm -m discovery -t sendtargets -I <iSCSINetName> -p <TargetIPAddress>:<TargetPort>
    ```

     \<iSCSINetName > は、ネットワークの一意/フレンドリ名です\<TargetIPAddress > は、iSCSI ターゲットの IP アドレスと\<TargetPort > iSCSI ターゲットのポートです。 

    ![iSCSITargetResults][3]

 
4.  ターゲットにログインします。

    ```bash
    sudo iscsiadm -m node -I <iSCSIIfaceName> -p TargetIPAddress -l
    ```

    \<iSCSIIfaceName > は、ネットワークの一意/フレンドリ名と\<TargetIPAddress > は、iSCSI ターゲットの IP アドレスです。

    ![iSCSITargetLogin][4]

5.  ISCSI ターゲットへの接続があることを確認します。

    ```bash
    sudo iscsiadm -m session
    ```

    ![iSCSIVerify][5]

 
6.  ISCSI 接続ディスクをチェックします。

    ```bash
    sudo grep "Attached SCSI" /var/log/messages
    ```
    ![30-iSCSIattachedDisks][7]

7.  ISCSI ディスク上の物理ボリュームを作成します。

    ```bash
    sudo pvcreate /dev/<devicename>
    ```

    \<デバイス名 > は、前の手順からデバイスの名前です。 

 
8.  ISCSI ディスク上のボリューム グループを作成します。 1 つのボリューム グループに割り当てられているディスクは、プールまたはコレクションと見なされます。 

    ```bash
    sudo vgcreate <VolumeGroupName> /dev/devicename
    ```

    \<VolumeGroupName > ボリューム グループの名前を指定し、 \<devicename > 手順 6 のデバイスの名前を指定します。 
 
9.  作成し、ディスクの論理ボリュームを確認します。

    ```bash
    sudo lvcreate -Lsize -n <LogicalVolumeName> <VolumeGroupName>
    ```
    
    \<サイズ > を作成するボリュームのサイズは、G (ギガバイト単位) を T (テラバイト) などを指定できます\<LogicalVolumeName >、論理ボリュームの名前を指定および\<VolumeGroupName > からボリューム グループの名前を指定します、前の手順。 

    次の例では、25 GB のボリュームを作成します。
 
    ![Create25GBVol][10]

10. 実行`sudo lvs`に作成された LVM を参照してください。
 
11. サポートされているファイル システムで論理ボリュームをフォーマットします。 EXT4 では、次の例を使用します。

    ```bash
    sudo mkfs.ext4 /dev/<VolumeGroupName>/<LogicalVolumeName>
    ```

    \<VolumeGroupName > は、前の手順からボリューム グループの名前です。 \<LogicalVolumeName > 前の手順で論理ボリュームの名前を指定します。  

12. システム データベースまたはデータの既定の場所に格納されているものは、次の手順に従います。 それ以外の場合、手順 13 に進みます。

   *    作業しているサーバーで SQL Server が停止していることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    スーパー ユーザーを完全にスイッチします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    sudo -i
    ```

   *    スイッチを mssql ユーザーにします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    su mssql
    ```

   *    SQL Server のデータを格納するファイルとログ ファイルを一時ディレクトリを作成します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > フォルダーの名前を指定します。 次の例では、/var/opt/mssql/TempDir という名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/TempDir
    ```
    
   *    SQL Server のデータとログ ファイルを一時ディレクトリにコピーします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > は、前の手順からフォルダーの名前です。
    
   *    ファイルがディレクトリであることを確認します。

    ```bash
    ls \<TempDir>
    ```
    \<TempDir > 手順 d からフォルダーの名前を指定します。

   *    既存の SQL Server データ ディレクトリからファイルを削除します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   *    ファイルが削除されたことを確認します。 次の図は、h での c からシーケンス全体の例を示します。

    ```bash
    ls /var/opt/mssql/data
    ```

    ![45-CopyMove][8]
 
   *    型`exit`ルート ユーザーに戻す。

   *    SQL Server データ フォルダーの iSCSI の論理ボリュームをマウントします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> /var/opt/mssql/data
    ``` 

    \<VolumeGroupName > ボリューム グループの名前を指定し、 \<LogicalVolumeName > が作成された論理ボリュームの名前を指定します。 次の構文の例では、前のコマンドからの論理ボリュームとボリューム グループと一致します。

    ```bash
    mount /dev/FCIDataVG1/FCIDataLV1 /var/opt/mssql/data
    ``` 

   *    Mssql マウントの所有者を変更します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    chown mssql /var/opt/mssql/data
    ```

   *    Mssql をマウントのグループの所有権を変更します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    chgrp mssql /var/opt/mssql/data
    ``` 

   *    Mssql ユーザーに切り替えます。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    su mssql
    ``` 

   *    一時ディレクトリ/var/opt/mssql/data からファイルをコピーします。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    cp /var/opt/mssql/TempDir/* /var/opt/mssql/data
    ``` 

   *    ファイルがあることを確認します。

    ```bash
    ls /var/opt/mssql/data
    ``` 
 
   *    入力`exit`mssql されません。
    
   *    入力`exit`ルートされません。

   *    SQL Server を起動します。 場合、すべてが正しくコピーされ、セキュリティが適用されて正しく、SQL Server 表示されますが開始します。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ``` 
 
   *    SQL Server を停止し、シャット ダウンがあることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ``` 

13. ユーザー データベースやバックアップなどのシステム データベース以外の次の手順に従います。 既定の場所を使用して、専用の場合は、手順 14 に進みます。

   *    スーパー ユーザーを指定するスイッチです。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    sudo -i
    ```

   *    SQL Server で使用されるフォルダーを作成します。 

    ```bash
    mkdir <FolderName>
    ```

    \<フォルダー名 > フォルダーの名前を指定します。 フォルダーの完全なパスを指定する必要があります。 適切な場所ではない場合。 次の例では、/var/opt/mssql/userdata という名前のフォルダーを作成します。

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    前の手順で作成されたフォルダー内の iSCSI の論理ボリュームをマウントします。 成功した場合は、すべての受信確認は受信しません。
    
    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName >、ボリューム グループの名前を指定します\<LogicalVolumeName > は、作成された論理ボリュームの名前を指定し、 \<FolderName > フォルダーの名前を指定します。 構文の例は、以下に示します。

    ```bash
    mount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

   *    Mssql を作成したフォルダーの所有権を変更します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    chown mssql <FolderName>
    ```

    \<フォルダー名 > が作成されたフォルダーの名前を指定します。 例を次に示します。

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```
  
   *    Mssql を作成したフォルダーのグループを変更します。 成功した場合は、すべての受信確認は受信しません。

    ```bash
    chown mssql <FolderName>
    ```

    \<フォルダー名 > が作成されたフォルダーの名前を指定します。 例を次に示します。

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```

   *    型`exit`にスーパー ユーザーになります。

   *    テストするには、そのフォルダーで、データベースを作成します。 次に示す例では、データベースを作成、コンテキストを切り替える、確認、ファイルは、OS レベルで存在し、一時的な場所を削除し、sqlcmd を使用します。 SSMS を使用することができます。
  
    ![50 ExampleCreateSSMS][9]

   *    共有のマウントを解除します。 

    ```bash
    sudo umount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName >、ボリューム グループの名前を指定します\<LogicalVolumeName > は、作成された論理ボリュームの名前を指定し、 \<FolderName > フォルダーの名前を指定します。 構文の例は、以下に示します。

    ```bash
    sudo umount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

14. その唯一の Pacemaker は、ボリューム グループをアクティブ化できるように、サーバーを構成します。

    ```bash
    sudo lvmconf --enable-halvm --services -startstopservices
    ```
 
15. サーバー上のボリューム グループの一覧を生成します。 何も表示されている iSCSI ディスクではないなどが使用、システムによって OS ディスクについてはします。

    ```bash
    sudo vgs
    ```

16. ファイル/etc/lvm/lvm.conf のアクティブ化の構成セクションを変更します。 次の行を構成します。

    ```bash
    volume_list = [ <ListOfVGsNotUsedByPacemaker> ]
    ```

    \<ListOfVGsNotUsedByPacemaker > は、FCI によって使用されていない手順 20 の出力からボリューム グループの一覧です。 コンマでは、それぞれ独立して引用符で囲まれたを配置します。 例を次に示します。

    ![55-ListOfVGs][11]
 
 
17. Linux の開始時に、ファイル システムをマウントします。 Pacemaker のみが iSCSI ディスクをマウントできることを確認するには、ルート ファイル システムのイメージを再構築します。 

    完了にしばらく時間がかかる場合がありますが、次のコマンドを実行します。 メッセージが表示されますないバックアップ成功した場合。

    ```bash
    sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r)
    ```

18. サーバーを再起動します。

19. FCI に参加する別のサーバーでは、手順 1 - 6 を実行します。 これにより、SQL Server に iSCSI ターゲットが表示されます。 
 
20. サーバー上のボリューム グループの一覧を生成します。 これにより、先ほど作成したボリューム グループが表示されます。 

    ```bash
    sudo vgs
    ``` 
23. SQL Server を起動し、このサーバーで開始することができることを確認します。

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```

24. SQL Server を停止し、それはシャット ダウンすることを確認します。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
25. FCI に参加する他のサーバーで手順 1. ~ 6. を繰り返します。

FCI を構成する準備が整いました。

|Distribution |トピック 
|----- |-----
|**HA アドオンの Red Hat Enterprise Linux** |[構成](sql-server-linux-shared-disk-cluster-configure.md)<br/>[操作](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server HA アドオン** |[構成](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>次の手順

[Linux 上の SQL Server のフェールオーバー クラスター インスタンスを構成します。](sql-server-linux-shared-disk-cluster-configure.md)

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
