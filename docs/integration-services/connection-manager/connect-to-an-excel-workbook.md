---
title: "Excel ブックに接続する |Microsoft ドキュメント"
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.custom: 
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
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2800075091835b2d6f2b07ee34e9b897fe86634e
ms.openlocfilehash: f8fb1db80ac1b750950a3401516b54af5ee29686
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="connect-to-an-excel-workbook"></a>Excel ブックに接続する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを Microsoft Office Excel ブックに接続するには、Excel 接続マネージャーが必要です。  
  
 これらの接続マネージャーは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [接続マネージャー] 領域または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードから作成できます。  
 
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Microsoft Excel および Access ファイルの接続コンポーネント
  
まだインストールしていない場合は、Microsoft Office ファイル用の接続コンポーネントをダウンロードする必要があります。 両方の Excel および Access ファイルの接続コンポーネントの最新バージョンをダウンロード: [Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)です。
  
最新のバージョンのコンポーネントは、以前のバージョンの Excel で作成されたファイルを開くことができます。

コンピューターには、Office の 32 ビット バージョンが存在する場合、コンポーネントの 32 ビット バージョンをインストールする必要があるし、およびも 32 ビット モードでパッケージを実行することを確認する必要があります。

Office 365 サブスクリプションがある場合は、し、Microsoft Access 2016 ランタイムではなく、Access データベース エンジン 2016 再頒布可能パッケージをダウンロードすることを確認します。 インストーラーを実行するときに、Office 実行するための コンポーネントと、ダウンロード サイド バイ サイドをインストールすることはできません、エラー メッセージを参照してください可能性があります。 このエラー メッセージをバイパスして、コンポーネントを正常にインストール、インストールを実行、quiet モードでコマンド プロンプト ウィンドウを開きを実行している、します。EXE ファイルと共にダウンロードした、`/quiet`スイッチします。 例:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="create-an-excel-connection-manager"></a>Excel 接続マネージャーを作成します。

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
  
  

