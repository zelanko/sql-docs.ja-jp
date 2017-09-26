---
title: "列の変換の詳細 ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 985ba8a478999a153b3bb32649b98c3e809fc5e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード)
  **[データ型マッピングの確認]** ページで個別の列の行をダブルクリックすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの **[列変換の詳細]** ダイアログ ボックスが表示されます。 このページでは、個々の列の詳細な変換情報を確認できます。 この情報には次の項目が含まれます。
-   ソースと変換先での列のデータ型。
-   データは、変換が必要な場合に、ウィザードによって実行される変換を入力します。
-   ウィザードが必要なデータ型変換を判断するために使用するデータ型マッピング ファイル。 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>[列変換の詳細] ページのスクリーン ショット 
 次のスクリーンショットは、ユーザーが **[データ型マッピングの確認]** ページで行をダブルクリックした後の、ウィザードの **[列変換の詳細]** ダイアログ ボックスです。 **[データ型マッピングの確認]** ページについては、「 [[データ型マッピングの確認]](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)」をご覧ください。
 
この例では、次のことが表示されます。
-   `PersonID`ソース SQL Server テーブルの列は型`int`です。 ウィザードが SQL Server Integration Services (SSIS) にこの型にマップ`DT_I4`MSSQLToSSIS10.xml データ型のマッピング ファイルを参照して、4 バイトの符号付き整数であるデータ型。
-   `PersonID` 、変換先の SQL Server テーブルの列が型も`int`します。 ウィザードにマップするには、この種類の SSIS データ型が同じです。
-   ウィザードでは、終了*この列では、変換は必要はありません*です。
 
  
 ![インポートおよびエクスポート ウィザードの列の変換ページ](../../integration-services/import-export-data/media/column-conversion.png "インポートおよびエクスポート ウィザードの列の変換 ページ") 
  
## <a name="whats-next"></a>次の操作  
 列変換の詳細を確認して **[OK]**をクリックすると、 **[列変換の詳細]** ダイアログ ボックスから **[データ型マッピングの確認]** ページに戻ります。 詳しくは、「 [[データ型マッピングの確認]](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)」をご覧ください。  

## <a name="see-also"></a>参照
[SQL Server インポートおよびエクスポート ウィザードのデータ型マッピング](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)

