---
title: セル内のアイテムの変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 2f666a5732a49050418917084554d630faabe679
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156969"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>セル内のアイテムの変更 (レポート ビルダーおよび SSRS)
  新しいレポート アイテムで置き換えることができるのは、テキスト ボックスや線、画像などの非コンテナー アイテムに限られています。 たとえば、テーブルをテキスト ボックス内にドラッグすると、テキスト ボックスをテーブルで置き換えることができます。  
  
 四角形、一覧、テーブル、マトリックスなどのコンテナー アイテムがセルに含まれている場合、新しいアイテムはコンテナー アイテムに置き換わるのではなく、コンテナー アイテムに追加されます。 コンテナー アイテムを新しいアイテムで置き換えるには、コンテナーを削除します。 コンテナー アイテムを削除すると、コンテナー アイテムはテキスト ボックスで置き換えられます。その後、テキスト ボックスを別のアイテムで置換できます。  
  
 既定では、テーブル、マトリックス、または一覧のデータ領域内にあるすべてのセルにテキスト ボックスが含まれています。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-an-item-within-a-cell"></a>セル内のアイテムを変更するには  
  
-   **[挿入]** タブの **[データ領域]** または **[レポート アイテム]** グループでレポートに追加するアイテムをクリックし、レポートをクリックします。 アイテムがレポートに追加されます。  
  
> [!NOTE]  
>  画像レポート アイテムをセルにドラッグすると、 **[画像のプロパティ]** ダイアログ ボックスが開きます。このダイアログ ボックスでは、画像をセルに追加する前に画像のソースなどのプロパティを設定できます。  
  
## <a name="see-also"></a>参照  
 [画像、テキスト ボックス、四角形、および行&#40;レポート ビルダーおよび SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [一覧 &#40;レポート ビルダーおよび SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
