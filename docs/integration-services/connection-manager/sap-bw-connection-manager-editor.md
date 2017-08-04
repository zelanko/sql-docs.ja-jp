---
title: "SAP BW 接続マネージャー エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sapbwconnectionmanager.f1
ms.assetid: ec970319-e749-4753-8675-9cf76ed99669
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a9f07a79e630550d7d0599026a91ee53f5b05d05
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-connection-manager-editor"></a>SAP BW 接続マネージャー エディター
  SAP Netweaver BW Version 7 システムへの接続に使用するプロパティを指定するには、 **[SAP BW 接続マネージャー エディター]** を使用します。  
  
 SAP BW 接続マネージャーは、SAP Netweaver BW Version 7 システムに SAP BW 変換元または変換先を接続します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 接続マネージャーの詳細については、「 [SAP BW 接続マネージャー](../../integration-services/connection-manager/sap-bw-connection-manager.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
 **SAP BW 接続マネージャー エディターを開くには**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 接続マネージャーが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[制御フロー]** タブ上にある [接続マネージャー] 領域で、次のいずれかの手順を実行します。  
  
    -   [SAP BW 接続マネージャー] をダブルクリックします。  
  
         — または —  
  
    -   [SAP BW 接続マネージャー] を右クリックし、 **[編集]**を選択します。  
  
## <a name="options"></a>オプション  
  
> [!NOTE]  
>  接続マネージャーを構成するために必要な値がわからない場合は、SAP 管理者に確認してください。  
  
 **クライアント**  
 システムのクライアント数を指定します。  
  
 **言語**  
 システムが使用する言語を指定します。 たとえば、英語の場合は、 **[EN]** を指定します。  
  
 **ユーザー名**  
 システムへの接続に使用するユーザー名を指定します。  
  
 **パスワード**  
 そのユーザー名のパスワードを指定します。  
  
 **単一のアプリケーション サーバーを使用する**  
 単一のアプリケーション サーバーに接続します。  
  
 負荷分散されたサーバーのグループに接続するには、 **[負荷分散を使用する]** オプションを使用します。  
  
 **ホスト**  
 単一のアプリケーション サーバーに接続する場合、ホスト名を指定します。  
  
> [!NOTE]  
>  このオプションは、 **[単一のアプリケーション サーバーを使用する]** オプションを選択している場合にのみ使用できます。  
  
 **システム数**  
 単一のアプリケーション サーバーに接続する場合、システム数を指定します。  
  
> [!NOTE]  
>  このオプションは、 **[単一のアプリケーション サーバーを使用する]** オプションを選択している場合にのみ使用できます。  
  
 **[負荷分散を使用する]**  
 負荷分散されたサーバーのグループに接続します。  
  
 単一のアプリケーション サーバーに接続するには、 **[単一のアプリケーション サーバーを使用する]** オプションを使用してください。  
  
 **メッセージ サーバー**  
 負荷分散されたサーバーのグループに接続する場合は、メッセージ サーバーの名前を指定します。  
  
> [!NOTE]  
>  このオプションは、 **[負荷分散を使用する]** オプションを選択している場合にのみ使用できます。  
  
 **[グループ]**  
 負荷分散されたサーバーのグループに接続する場合は、サーバー グループの名前を指定します。  
  
> [!NOTE]  
>  このオプションは、 **[負荷分散を使用する]** オプションを選択している場合にのみ使用できます。  
  
 **SID**  
 負荷分散されたサーバーのグループに接続する場合は、接続のシステム ID を指定します。  
  
> [!NOTE]  
>  このオプションは、 **[負荷分散を使用する]** オプションを選択している場合にのみ使用できます。  
  
 **ログ ディレクトリ**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW のコンポーネントに対するログを有効にします。  
  
 ログを有効にするには、RFC の各関数呼び出しの前後に作成されたログ ファイルのディレクトリを指定します (このログ機能は、XML 形式で多くのログ ファイルを作成します。 これらのログ ファイルには転送されるデータのすべての行も含まれるため、大量のディスク領域を消費する可能性があります)。  
  
> [!IMPORTANT]  
>  転送されるデータに機密情報が含まれている場合、ログ ファイルには機密情報も含まれることになります。  
  
 ログ ディレクトリを指定するには、ディレクトリ パスに手動で入力するか、 **[参照]** をクリックし、ログ ディレクトリを参照します。  
  
 ログ ディレクトリを選択しないと、ログ記録は有効になりません。  
  
 **[参照]**  
 ログ ディレクトリのフォルダーを参照して選択します。  
  
 **[接続テスト]**  
 指定した値を使用して接続をテストします。 **[接続テスト]**をクリックすると、接続が成功または失敗したかを示すメッセージ ボックスが表示されます。  
  
## <a name="see-also"></a>参照  
 [Microsoft Connector for SAP BW の F1 ヘルプ](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
