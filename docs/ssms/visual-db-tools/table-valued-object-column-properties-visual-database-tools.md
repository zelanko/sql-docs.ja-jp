---
title: テーブル値オブジェクト (列) のプロパティ
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.QueryViewColumn
ms.assetid: 212d9bcd-aded-4313-a6b9-d7e2270e5954
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: d5c82466168714f6a58055e1ed50959602318ef3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75242163"
---
# <a name="table-valued-object-column-properties-visual-database-tools"></a>テーブル値オブジェクト (列) のプロパティ (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
クエリ デザイナーとビュー デザイナーの **[ダイアグラム]** ペインでテーブル値オブジェクト内の列を選択したときに、このプロパティが表示されます。  
  
> [!NOTE]  
> このトピックでは、プロパティを五十音順ではなくカテゴリ別に示しています。  
  
> [!NOTE]  
> 使用中の設定やエディションに応じて、表示されるダイアログ ボックスとメニュー コマンドがヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** を選択してください。  
  
**[IDENTITY] カテゴリ**  
展開すると、 **[名前]** プロパティが表示されます。  
  
**名前**  
選択した列の名前が表示されます。  
  
**クエリ デザイナー カテゴリ**  
展開すると、 **[NULL を許容]** 、 **[照合順序]** 、 **[長さ]** 、 **[データ型]** 、 **[精度]** 、 **[スケール]** 、 **[サイズ]** のプロパティが表示されます。  
  
**[NULL を許容]**  
列のデータ型で NULL が許容されるかどうかが表示されます。  
  
**Collation**  
選択した列における照合順序の設定が表示されます。 照合順序は、Table Designer の [列のプロパティ] タブで設定できます。  
  
**[データ型]**  
選択した列のデータ型が表示されます。  
  
**[データ型]**  
選択した列のデータ型で許容される文字または数字の数が表示されます。 このプロパティは、文字に基づくデータ型にのみ使用できます。  
  
> [!NOTE]  
> バイト単位の大きさについては、以降に示す **[サイズ]** プロパティの説明を参照してください。  
  
**[精度]**  
数値データ型で許容される最大桁数が表示されます。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。  
  
**スケール**  
数値データ型の小数点の右側にある桁数の最大数が表示されます。 この値は、有効桁数以下である必要があります。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。  
  
**[サイズ]**  
列のデータ型で許容されるサイズがバイト単位で表示されます。 たとえば、nchar データ型の長さが 10 (文字数) でも、Unicode 文字セットの場合のサイズは 20 になります。  
  
