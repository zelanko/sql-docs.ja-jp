---
title: "OLE DB 接続マネージャーの |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94287024cf1a79384f888406a0c111644d6696fc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="ole-db-connection-manager"></a>OLE DB 接続マネージャー
  OLE DB 接続マネージャーを使用すると、パッケージは OLE DB プロバイダーを使用してデータ ソースに接続できます。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する OLE DB 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用できます。    
    
> [!NOTE]    
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB プロバイダーでは、マルチサブネット フェールオーバー クラスタリングの新しい接続文字列キーワード (MultiSubnetFailover=True) はサポートされません。 詳細については、 [SQL Server リリース ノート](http://go.microsoft.com/fwlink/?LinkId=247824) および www.mattmasson.com のブログ記事「 [AlwaysOn マルチサブネット フェールオーバーと SSIS](http://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)」を参照してください。    
    
> [!NOTE]    
>  データ ソースが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 または [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007 である場合、Excel または Access の以前のバージョンとは異なるデータ プロバイダーが必要になります。 詳細については、「 [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) 」および「 [Access データベースに接続する](../../integration-services/connection-manager/connect-to-an-access-database.md)」を参照してください。    
    
 いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] タスクとデータ フロー コンポーネントは、OLE DB 接続マネージャーを使用します。 たとえば、OLE DB ソースと OLE DB 変換先は、この接続マネージャーを使用してデータの抽出と読み込みを行います。また、SQL 実行タスクは、この接続マネージャーを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、クエリを実行できます。    
    
 OLE DB 接続マネージャーは、C++ などの言語を使用するアンマネージ コードで記述されたカスタム タスク内で、OLE DB データ ソースにアクセスするためにも使用されます。    
    
 OLE DB 接続マネージャーをパッケージに追加すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に OLE DB 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの **Connections** コレクションに追加します。    
    
 接続マネージャーの **ConnectionManagerType** プロパティは、 **OLEDB**に設定されます。    
    
 OLE DB 接続マネージャーは、次の方法で構成できます。    
    
-   選択したプロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。    
    
-   プロパイダによっては、接続先のデータ ソースの名前を指定します。    
    
-   選択したプロバイダーに適したセキュリティ資格情報を指定します。    
    
-   接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。    
    
## <a name="logging"></a>ログ記録    
 OLE DB 接続マネージャーによる外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、OLE DB 接続マネージャーによる外部データ ソースへの接続に関するトラブルシューティングを行うことができます。 OLE DB 接続マネージャーによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択する必要があります。 詳細については、「 [パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。    
    
## <a name="configuration-of-the-oledb-connection-manager"></a>OLEDB 接続マネージャーの構成    
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [OLE DB 接続マネージャーの構成](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)」を参照してください。 プログラムによって接続マネージャーを構成する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** クラスのドキュメントを参照してください。    
    
## <a name="related-content"></a>関連コンテンツ    
    
-   social.technet.microsoft.com の Wiki の記事「 [SSIS から Oracle への接続](http://go.microsoft.com/fwlink/?LinkId=220670) 」    
    
-   carlprothman.net の [OLE DB プロバイダー用接続文字列](http://go.microsoft.com/fwlink/?LinkId=220744)に関する技術記事    
    
## <a name="see-also"></a>参照    
 [OLE DB ソース](../../integration-services/data-flow/ole-db-source.md)     
 [OLE DB 変換先](../../integration-services/data-flow/ole-db-destination.md)     
 [SQL 実行タスク](../../integration-services/control-flow/execute-sql-task.md)     
 [Integration Services & #40 です。SSIS &#41;接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
