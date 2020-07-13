---
title: Enable-[書き戻しの無効化] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitiondesigner.writebackenabledisable.f1
ms.assetid: 2d254393-3f0d-4b70-8b98-87159f9f3639
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac29fc0d1539ae75ca5f54ad48f1779692b9a6df
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528410"
---
# <a name="enable-disable-writeback-dialog-box-analysis-services---multidimensional-data"></a>有効/[書き戻しの無効化] ダイアログボックス (Analysis Services-多次元データ)
  **[書き戻しの有効化]/[書き戻しの無効化]** ダイアログ ボックスを使用すると、キューブ内のメジャー グループの書き戻しを有効または無効にできます。 メジャー グループの書き戻しを有効にすると、書き戻しパーティションが定義され、そのメジャー グループの書き戻しテーブルが作成されます。 メジャー グループの書き戻しを無効にすると、書き戻しパーティションが削除されます。ただし、予期しないデータの消失を避けるために、書き戻しテーブルは削除されません。 **[書き戻しの有効化]/[書き戻しの無効化]** ダイアログ ボックスを表示するには、次の操作を行います。  
  
-   キューブ デザイナーの **[パーティション]** タブの **[メジャー グループ]** ペインの **[書き戻しの設定]** をクリックします。  
  
-   キューブ デザイナーの **[パーティション]** タブの **[メジャー グループ]** ペインの **[パーティション]** グリッドでパーティションを右クリックし、ショートカット メニューの **[書き戻しの設定]** をクリックします。  
  
## <a name="options"></a>オプション  
 **テーブル名**  
 選択したパーティションに対して作成する書き戻しテーブルの名前を入力します。 書き戻しテーブルには、クライアント アプリケーションからのメジャー グループへの変更が格納されます。  
  
> [!NOTE]  
>  書き戻しが有効でない場合、このオプションは無効になります。  
  
 **データ ソース**  
 書き戻しテーブルを格納するデータ ソースを選択します。  
  
> [!NOTE]  
>  書き戻しが有効でない場合、このオプションは無効になります。  
  
 **[新規作成]**  
 クリックすると、 **[接続マネージャー]** ダイアログ ボックスが表示されます。このダイアログ ボックスで、書き戻しテーブルを格納する新しいデータ ソースを定義します。  
  
> [!NOTE]  
>  書き戻しが有効でない場合、このオプションは無効になります。  
  
  
