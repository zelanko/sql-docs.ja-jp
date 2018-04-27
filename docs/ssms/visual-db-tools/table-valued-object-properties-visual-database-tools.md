---
title: テーブル値オブジェクトのプロパティ (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdt.designers.properties.TVO
ms.assetid: eaf06cbf-8242-4483-894f-80ae02a4840e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80af649c5ab068f4aebfc357bdd565577ce30046
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="table-valued-object-properties-visual-database-tools"></a>テーブル値オブジェクトのプロパティ (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
これらのプロパティは、 **クエリおよびビュー デザイナー**でテーブル値オブジェクトを選択したときに、[プロパティ] ウィンドウに表示されます。 テーブル値オブジェクトは、ビュー、シノニム、派生テーブル、またはテーブル値関数です。 特に指定しない限り、 **[プロパティ]** ウィンドウのこれらのプロパティは読み取り専用です。  
  
> [!NOTE]  
> このトピックでは、プロパティを五十音順ではなくカテゴリ別に示しています。  
  
> [!NOTE]  
> 使用中の設定やエディションに応じて、表示されるダイアログ ボックスとメニュー コマンドがヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** を選択してください。  
  
**[IDENTITY] カテゴリ**  
展開すると、 **[オブジェクト名]** プロパティと **[TVO 型]** プロパティが表示されます。  
  
**名前**  
選択されたテーブル値オブジェクトの名前を表示します。  
  
**[TVO 型]**  
テーブル値オブジェクトの種類を表示します。 ベース テーブル、ビュー、テーブル値関数、または派生テーブルです。  
  
**クエリ デザイナー カテゴリ**  
展開すると、 **[エイリアス]**、 **[列一覧]**、 **[名前]**、および **[パラメーター リスト]** のプロパティが表示されます。  
  
**[エイリアス]**  
選択されたテーブル値オブジェクトの別名を表示します。 別名を追加または変更するには、フィールドに入力します。  
  
**[列一覧]**  
選択されたテーブル値オブジェクトに含まれている列を表示します。 別のウィンドウに表示する場合は、[列一覧] をクリックしてから、プロパティの右の [...] をクリックします。  
  
**[名前]**  
選択したテーブル値オブジェクトの名前を表示します。オブジェクトのスキーマまたはデータ ソースなどの追加情報が含まれます。  
  
**[パラメーター リスト]**  
選択したテーブル値関数用に定義されたパラメーターを表示します。 パラメーターの値を定義する場合は、[パラメーター リスト] をクリックしてから、プロパティの右の [...] をクリックします。 [関数パラメーター] ダイアログ ボックスで、値を入力します。 このプロパティは、テーブル値関数が選択された場合のみ使用できます。  
  
