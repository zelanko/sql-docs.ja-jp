---
title: OLE DB 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98e9684e590493a21c9b0f526eb48bf4985c5d8a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434229"
---
# <a name="ole-db-connection-manager"></a>OLE DB 接続マネージャー
  OLE DB 接続マネージャーを使用すると、パッケージは OLE DB プロバイダーを使用してデータ ソースに接続できます。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する OLE DB 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用できます。  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB プロバイダーでは、マルチサブネット フェールオーバー クラスタリングの新しい接続文字列キーワード (MultiSubnetFailover=True) はサポートされません。 詳細については、www.mattmasson.com の[リリースノート](https://go.microsoft.com/fwlink/?LinkId=247824)と、の[AlwaysOn マルチサブネットフェールオーバーおよび SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)に関するブログ記事を参照し SQL Server てください。  
  
 いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] タスクとデータフローコンポーネントでは、OLE DB 接続マネージャーを使用します。 たとえば、OLE DB ソースと OLE DB 変換先は、この接続マネージャーを使用してデータの抽出と読み込みを行います。また、SQL 実行タスクは、この接続マネージャーを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、クエリを実行できます。  
  
 OLE DB 接続マネージャーは、C++ などの言語を使用するアンマネージ コードで記述されたカスタム タスク内で、OLE DB データ ソースにアクセスするためにも使用されます。  
  
 OLE DB 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に OLE DB 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。  
  
 接続マネージャーの `ConnectionManagerType` プロパティは、`OLEDB` に設定されます。  
  
 OLE DB 接続マネージャーは、次の方法で構成できます。  
  
-   選択したプロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。  
  
-   プロパイダによっては、接続先のデータ ソースの名前を指定します。  
  
-   選択したプロバイダーに適したセキュリティ資格情報を指定します。  
  
-   接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。  
  
## <a name="logging"></a>ログの記録  
 OLE DB 接続マネージャーによる外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、OLE DB 接続マネージャーによる外部データ ソースへの接続に関するトラブルシューティングを行うことができます。 OLE DB 接続マネージャーが外部データプロバイダーに対して行う呼び出しをログに記録するには、パッケージログ記録を有効にし、パッケージレベルで**Diagnostic**イベントを選択します。 詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。  
  
## <a name="configuration-of-the-oledb-connection-manager"></a>OLEDB 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [OLE DB 接続マネージャーの構成](../configure-ole-db-connection-manager.md)」を参照してください。 プログラムによって接続マネージャーを構成する方法の詳細については、開発者ガイドの **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** クラスのドキュメントを参照してください。  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   social.technet.microsoft.com の Wiki の記事「 [SSIS から Oracle への接続](https://go.microsoft.com/fwlink/?LinkId=220670) 」  
  
-   carlprothman.net の [OLE DB プロバイダー用接続文字列](https://go.microsoft.com/fwlink/?LinkId=220744)に関する技術記事  
  
## <a name="see-also"></a>関連項目  
 [OLE DB ソース](../data-flow/ole-db-source.md)   
 [OLE DB の宛先](../data-flow/ole-db-destination.md)   
 [SQL 実行タスク](../control-flow/execute-sql-task.md)   
 [Integration Services &#40;SSIS&#41; の接続](integration-services-ssis-connections.md)  
  
  
