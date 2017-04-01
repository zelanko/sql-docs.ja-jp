---
title: "dBASE ファイルまたはその他の DBF ファイルに接続する | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DBF ファイルへの接続"
  - "dBase ファイル"
  - "DBF ファイル"
ms.assetid: b0e8c831-9f96-475c-82a4-4f5b02692752
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# dBASE ファイルまたはその他の DBF ファイルに接続する
  OLE DB 接続マネージャーを使用して Microsoft OLE DB Provider for Jet 4.0 を選択すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで dBASE データベース ファイルまたは .DBF データベース ファイルに接続できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SQL Server インポートおよびエクスポート ウィザードでは、dBASE ファイルやその他の DBF ファイルからのインポート、またはこれらのファイルへのエクスポートはサポートされません。 Microsoft Access または Microsoft Excel を使用して DBF ファイルから Access データベースまたは Excel ワークシートにデータをインポートした後、SQL Server インポートおよびエクスポート ウィザードを使用できます。  
  
### dBase ファイルまたはその他の DBF ファイルに接続するように接続マネージャーを構成するには  
  
1.  パッケージに新しい OLE DB 接続マネージャーを追加します。 詳細については、「[パッケージの接続マネージャーを追加、削除、または共有する](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md)」を参照してください。  
  
2.  **[接続マネージャー]** ダイアログ ボックスの **[接続]** ページで、**[プロバイダー]** としてネイティブ OLE DB\Microsoft Jet 4.0 OLE DB Provider を選択します。  
  
3.  DBF ファイルを操作するとき、フォルダーはデータベースを表し、各 DBF ファイルはテーブルを表します。 したがって、**[データベース ファイル名]** ボックスには、DBF ファイルが存在するフォルダーのパスを含める必要があります。ファイル名自体は含めないでください。 フォルダー パスを入力するか、コピーして貼り付けます。または、**[参照]** ボタンをクリックして DBF ファイルを選択し、フォルダー パスの末尾からファイル名を削除します。  
  
4.  **[接続マネージャー]** ダイアログ ボックスの **[すべて]** ページで、拡張プロパティの値として [Extended Properties] ボックスに「**dBASE III**」、「**dBASE IV**」、または「**dBASE 5.0**」と入力します。  
  
5.  **[接続テスト]** をクリックして、入力した値を検証します。 "接続テストに成功しました。" というメッセージが表示されます。 **[OK]** をクリックして、メッセージ ボックスを閉じます。  
  
6.  **[OK]** をクリックして、接続マネージャーの構成を保存します。  
  
7.  接続マネージャーをパッケージのデータ フローで使用するため、OLE DB の変換元または変換先を選択して、上記の手順に従って作成した接続マネージャーを使用するように構成します。  
  
## 参照  
 [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  