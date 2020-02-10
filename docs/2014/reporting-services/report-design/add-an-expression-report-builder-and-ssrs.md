---
title: 式の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 54505266a77c8baee7f39633ebccd0a5ab5708a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106740"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a>式の追加 (レポート ビルダーおよび SSRS)
  レポート アイテムのプロパティ、フィルター、グループ、並べ替え順、接続文字列、パラメーター値などを定義するために、レポートには随所に式が使用されます。 式は等号 (=) で始まり、で[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]記述されています。 式は、評価結果とレポート レイアウト要素を組み合わせるレポート プロセッサによって実行時に評価されます。  
  
 式には単純式と複合式があります。 単純式は、組み込みコレクションの 1 つのアイテムを指します。 複合式には、定数、演算子、グローバル コレクションのアイテム、および関数呼び出しを含めることができます。 詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a>テキスト ボックスに式を追加するには  
  
-   
  **[デザイン]** ビューで、式を追加するデザイン画面のテキスト ボックスをクリックします。  
  
    -   単純式の場合、テキスト ボックスに式の表示テキストを入力します。 たとえば、Sales データセット フィールドには、 `[Sales]`を入力します。  
  
    -   複合式の場合、テキスト ボックスを右クリックし、 **[式]** をクリックします。 
  **[式]** ダイアログ ボックスが表示されます。 式ペインの '=' の後に式を入力するか、対話形式で式を作成し、[OK] をクリックします。  
  
         式がデザイン画面に `<<Expr>>`として表示されます。  
  
## <a name="see-also"></a>参照  
 [テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [テキスト ボックス &#40;レポート ビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [フィルター式の例 &#40;レポートビルダーと SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)   
 [グループ式の例 &#40;レポート ビルダーおよび SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [[式] ダイアログボックス &#40;レポートビルダー&#41;](../expression-dialog-box-report-builder.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [SSRS&#41;&#40;レポートにコードを追加する](add-code-to-a-report-ssrs.md)  
  
  
