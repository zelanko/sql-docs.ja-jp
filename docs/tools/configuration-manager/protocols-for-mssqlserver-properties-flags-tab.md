---
title: "プロトコルの MSSQLSERVER プロパティ ([フラグ] タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQLSERVER property protocols
ms.assetid: 4d38e6e9-f95f-4e79-ae45-89f631037528
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6ed0d315ee6b469fddcf3f6e10d8016f43653eda
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="protocols-for-mssqlserver-properties-flags-tab"></a>[MSSQLSERVER のプロトコルのプロパティ] ダイアログ ボックス ([フラグ] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]証明書がサーバーにインストールされているときに使用、**フラグ**タブで、 **MSSQLSERVER プロパティのプロトコル** ダイアログ ボックスを表示またはプロトコルの暗号化を指定し、インスタンスのオプションを非表示にします。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の設定を有効または無効にするには、 **[ForceEncryption]** を再起動する必要があります。  
  
 接続を暗号化するには、証明書を付けて [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を提供する必要があります。 証明書がインストールされていない場合、インスタンスが起動されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により自己署名入りの証明書が生成されます。 この自己署名入りの証明書は、信頼されている証明機関から発行された証明書の代わりに使用することはできますが、この証明書では認証機能や否認不可機能は提供されません。  
  
> [!CAUTION]  
>  自己署名入りの証明書を使用して暗号化された SSL (Secure Sockets Layer) 接続では、強力なセキュリティは提供されません。 このような接続では、man-in-the-middle アタックによる被害を受けやすくなります。 実稼働環境やインターネットに接続しているサーバーでは、自己署名入りの証明書を使用した SSL 接続は使用しないことをお勧めします。  
  
 暗号化の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続の暗号化」をご覧ください。  
  
 ログイン プロセスは常に暗号化されます。 **[ForceEncryption]** が **[はい]**に設定されているときは、クライアントとサーバーのすべての接続が暗号化されます。そのため、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] に対するクライアント接続は、サーバー証明書のルート機関を信頼するように構成する必要があります。 詳細については、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] オンライン ブックの「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への暗号化接続を有効にする方法 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー)」を参照してください。  
  
## <a name="cluster-servers"></a>クラスター サーバー  
 フェールオーバー クラスターで暗号化を使用する場合は、フェールオーバー クラスター内のすべてのノードに対して、仮想サーバーの完全に修飾された DNS 名でサーバー証明書をインストールする必要があります。 たとえば、"test1 ノード名前付きの 2 ノード クラスターを使用する場合。*\<会社 >*.com"および"test2 *。\<会社 >*.com"の証明書をインストールする必要があります"virtsql"という仮想サーバー、および"virtsql *。\<会社 >*.com"を両方のノードです。 その後、 **SQL Server 構成マネージャー** で **[ForceEncryption]** チェック ボックスをオンにすれば、フェールオーバー クラスターの暗号化を構成できます。  
  
## <a name="options"></a>および  
 **[ForceEncryption]**  
 プロトコルを強制的に暗号化します。 暗号化とは、データを読み取り不可能な形式に変更することにより、秘密情報を保護する方法です。 仮に転送プロセスで転送パケットが閲覧されることがあっても、暗号化していればデータは安全です。 チャネル バインドを使用するには、 **[強制的に暗号化]** を **[オン]** に設定し、 **[詳細設定]** タブで **[拡張保護]** を構成します。  
  
 **[HideInstance]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [参照] **ボタンを使用してこの** インスタンスを表示しようとするクライアントに対してこのインスタンスを公開しません。 サーバー上の名前付きのインスタンスの場合、接続するには、クライアント アプリケーションはプロトコル エンドポイント情報を指定する必要があります。 たとえば、 **tcp:server,5000**など、ポート番号または名前付きパイプ名を指定します。 詳しくは、「 [Logging In to SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)」をご覧ください。  
  
 詳細については、オンライン ブックの「データベース エンジンへの暗号化接続を有効にする方法 (構成マネージャー)」を参照してください。  
  
  
