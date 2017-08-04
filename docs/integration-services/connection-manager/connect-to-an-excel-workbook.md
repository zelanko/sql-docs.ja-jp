---
title: "Excel ブックに接続する |Microsoft ドキュメント"
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel [Integration Services]
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b36b92c9beb840f6a2ea66250a5a025aa587acef
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-excel-workbook"></a>Excel ブックに接続する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを Microsoft Office Excel ブックに接続するには、Excel 接続マネージャーが必要です。  
  
 これらの接続マネージャーは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [接続マネージャー] 領域または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードから作成できます。  
  
 **Microsoft Excel および Access ファイルのプロバイダーとドライバー**  
  
 まだインストールしていない場合は、Microsoft Office ファイル用の OLE DB プロバイダーとドライバーをダウンロードする必要があることがあります。 以降のバージョンのプロバイダーは、以前のバージョンの Excel で作成したファイルを開くことができます。  
  
 コンピューターに 32 ビット バージョンの Office が存在する場合は、32 ビット バージョンのドライバーをインストールする必要があるほか、32 ビット モードで作成したウィザードまたは Integration Services パッケージが実行されるようにする必要があります。  
  
|Microsoft Office のバージョン|ダウンロード|  
|------------------------------|--------------|  
|2007|[2007 Office system ドライバー: データ接続コンポーネント](https://www.microsoft.com/en-us/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/en-us/download/details.aspx?id=39358)|  
  
### <a name="to-create-an-excel-connection-manager-from-the-connection-managers-area"></a>[接続マネージャー] 領域から Excel 接続マネージャーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、パッケージを開きます。  
  
2.  **[接続マネージャー]** 領域内を右クリックし、 **[新しい接続]**を選択します。  
  
3.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで、 **[Excel]**を選択し、接続マネージャーを構成します。  
  
     この接続マネージャーで使用可能な構成オプションの詳細については、「 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager-editor.md)」を参照してください。  
  
### <a name="to-create-an-excel-connection-from-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードから Excel 接続を作成するには  
  
1.  32 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを起動します。  
  
2.  **[データ ソースの選択]** ページの **[データ ソース]**で **[Microsoft Excel]**を選択して、Excel 接続を構成します。  
  
     この接続の種類で使用可能な構成オプションの詳細については、「 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager-editor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Access データベースに接続する](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  
