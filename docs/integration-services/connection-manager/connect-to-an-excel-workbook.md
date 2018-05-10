---
title: Excel ブックに接続する | Microsoft Docs
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Excel [Integration Services]
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 62c9d7b4de0b764ff7208b0fa077ec12b58dec60
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-an-excel-workbook"></a>Excel ブックに接続する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを Microsoft Office Excel ブックに接続するには、Excel 接続マネージャーが必要です。  
  
 これらの接続マネージャーは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [接続マネージャー] 領域または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードから作成できます。  
 
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Microsoft Excel および Access ファイルの接続コンポーネント
  
Microsoft Office ファイルの接続コンポーネントがまだインストールされていない場合は、必要に応じてダウンロードします。 [Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)で、Excel と Access の両方のファイルの最新バージョンの接続コンポーネントをダウンロードします。
  
以前のバージョンの Excel で作成したファイルは、最新バージョンのコンポーネントで開くことができます。

コンピューターに 32 ビット バージョンの Office が存在する場合は、32 ビット バージョンのコンポーネントをインストールする必要があるほか、32 ビット モードでパッケージが実行されるようにする必要があります。

Office 365 サブスクリプションがある場合は、Microsoft Access 2016 ランタイムではなく、必ず Access データベース エンジン 2016 再頒布可能パッケージをダウンロードしてください。 インストーラーを実行するときに、ダウンロードを Office のクイック実行コンポーネントとサイド バイ サイドでインストールできないことを示すエラー メッセージが表示される場合があります。 このエラー メッセージを回避して、コンポーネントを正常にインストールするには、コマンド プロンプト ウィンドウを開き、`/quiet` スイッチを使用してダウンロードした .EXE ファイルを実行して、Quiet モードでインストールを実行します。 例 :

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="create-an-excel-connection-manager"></a>Excel 接続マネージャーの作成

### <a name="to-create-an-excel-connection-manager-from-the-connection-managers-area"></a>[接続マネージャー] 領域から Excel 接続マネージャーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、パッケージを開きます。  
  
2.  **[接続マネージャー]** 領域内を右クリックし、 **[新しい接続]** を選択します。  
  
3.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで、 **[Excel]** を選択し、接続マネージャーを構成します。  
  
     この接続マネージャーで使用可能な構成オプションの詳細については、「 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager-editor.md)」を参照してください。  
  
### <a name="to-create-an-excel-connection-from-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードから Excel 接続を作成するには  
  
1.  32 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを起動します。  
  
2.  **[データ ソースの選択]** ページの **[データ ソース]** で **[Microsoft Excel]** を選択して、Excel 接続を構成します。  
  
     この接続の種類で使用可能な構成オプションの詳細については、「 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager-editor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Access データベースに接続する](../../integration-services/connection-manager/connect-to-an-access-database.md)  
  
  
