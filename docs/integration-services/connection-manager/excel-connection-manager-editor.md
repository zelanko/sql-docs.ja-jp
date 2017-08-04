---
title: "[Excel 接続マネージャー エディター] |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c4060736f824becd05fecceba0b162b45f0fed4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="excel-connection-manager-editor"></a>Excel 接続マネージャー
  **[Excel 接続マネージャー]** ダイアログ ボックスを使用すると、既存または新規の [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ブック ファイルへの接続を追加できます。  
  
 Excel 接続マネージャーの詳細については、「 [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[Excel ファイル パス]**  
 既存または新規の Excel ブック ファイル (.xls) のパスおよびファイル名を入力します。  
  
> [!NOTE]  
>  パスワードで保護された Excel ファイルには接続できません。  
  
> [!WARNING]  
>  既存ではない新規のファイルを示す **[Excel 接続]** を選択し、 **[Excel シートの名前]** で **[新規]** をクリックすると、 **Excel 変換先エディター**は自動的に Excel ファイルを作成します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、Excel ファイルが存在するフォルダー、または新しいファイルを作成するフォルダーを指定します。  
  
 **[Excel バージョン]**  
 ファイルを作成するために使用した Microsoft Excel のバージョンを指定します。  
  
 **[先頭行に列名を含める]**  
 選択されているワークシートのデータの 1 行目に列名が含まれているかどうかを指定します。 このオプションの既定値は **[true]**です。  
  
## <a name="providers-and-drivers-for-microsoft-excel-and-access-file"></a>Microsoft Excel および Access ファイルのプロバイダーとドライバー  
 まだインストールしていない場合は、Microsoft Office ファイル用の OLE DB プロバイダーとドライバーをダウンロードする必要があることがあります。 以降のバージョンのプロバイダーは、以前のバージョンの Excel で作成したファイルを開くことができます。  
  
 コンピューターに 32 ビット バージョンの Office が存在する場合は、32 ビット バージョンのドライバーをインストールする必要があるほか、32 ビット モードで作成したウィザードまたは Integration Services パッケージが実行されるようにする必要があります。  
  
|Microsoft Office のバージョン|ダウンロード|  
|------------------------------|--------------|  
|2007|[2007 Office system ドライバー: データ接続コンポーネント](https://www.microsoft.com/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Excel をループ処理のファイルおよび Foreach ループ コンテナーを使用してテーブル](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
