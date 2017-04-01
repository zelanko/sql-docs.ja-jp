---
title: "SQL Server での R ランタイムのセキュリティに関する考慮事項 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# SQL Server での R ランタイムのセキュリティに関する考慮事項
  このトピックでは、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を操作するためのセキュリティに関する考慮事項の概要を示します。  
  
 サービスの管理の詳細、および R スクリプトの実行に使用されるユーザー アカウントのプロビジョニング方法については、「 [Configure and Manage Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md)」を参照してください。  
  
## ファイアウォールを使用して、R によるネットワーク アクセスを制限するには  
 推奨されるインストール方法では、Windows ファイアウォール ルールを使用すると、R ランタイム プロセスからのすべての発信ネットワーク アクセスがブロックされます。 R ランタイム プロセスによって、パッケージのダウンロード、および悪意のある可能性があるその他のネットワーク呼び出しが実行されないように、ファイアウォール ルールを作成する必要があります。  
  
 R ランタイムによるネットワーク アクセスをブロックするには、Windows ファイアウォール (または別のファイアウォール) を有効にすることを強くお勧めします。  
  
 別のファイアウォール プログラムを使用している場合にも、ローカル ユーザー アカウント用、またはユーザー アカウント プールによって表されるグループ用のルールを設定することで、R ランタイムの送信ネットワーク接続をブロックするためのルールを作成できます。   
詳細については、「 [Configure and Manage Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md)」を参照してください。  
  
## リモート コンピューティングのコンテキストでサポートされる認証メソッド 
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 間の接続を作成するときに Windows 統合認証と SQL ログインの両方をサポート [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とリモート データ サイエンス クライアントです。 
  
 など、ラップトップ上 R ソリューションを開発して、SQL Server コンピューターに対して計算を実行する場合は作成する SQL Server データ ソース r でを使用して、 **rx** Windows 資格情報に基づいて、関数との接続文字列を定義します。 変更すると、 _コンテキストを計算_ SQL Server コンピューター、ラップトップでは、Windows アカウントに必要なアクセス許可がある場合すべての R コードの実行元 SQL Server コンピューターにします。 さらに、R コードの一部として実行された SQL クエリは、同様に、資格情報で実行されます。 
 
 SQL ログインは、SQL Server データ ソースの接続文字列でも使用できますが、ログインの使用では、SQL Server インスタンスでは、混合モード認証が使用できる必要があります。
 
 ### 暗黙の認証
  
 一般に、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] R ランタイムを起動し、独自のアカウントでの R スクリプトを実行します。 ただし、R スクリプトでは、ODBC 呼び出した場合、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ODBC 呼び出しが失敗しないようにするコマンドを送信したユーザーの資格情報を偽装します。 これと呼ばれる *暗黙認証*します。 
 
 > [!IMPORTANT] 
 >
 > 暗黙の認証を行う、ワーカー アカウントを含む Windows ユーザー グループ (既定では、 **SQLRUser**) インスタンス」、「このアカウントが、インスタンスに接続するアクセス許可を付与する必要があります、master データベースにアカウントが必要です。  
  
## 保存時の暗号化がサポートされていない  
 R ランタイムとのデータの送受信については、透過的なデータ暗号化はサポートされていません。 その結果、保存時の暗号化は、R スクリプトで使用するデータ、ディスクに保存されるデータ、または保存された中間結果のいずれにも適用 **されません** 。  
 
 ## 参照
 [ここでリンクの説明を入力してください。](../../advanced-analytics/r-services/configuration-sql-server-r-services.md) 
  