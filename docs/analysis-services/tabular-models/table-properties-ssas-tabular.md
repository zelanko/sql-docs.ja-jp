---
title: テーブルのプロパティ |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7cfe22cf11a49b7597e665221b272078213470be
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="table-properties"></a>Table Properties 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  この記事では、表形式モデル テーブルのプロパティについて説明します。 ここで説明するプロパティは、ソースのどの列をインポートするかを定義する [テーブルのプロパティの編集] ダイアログ ボックスのプロパティとは異なります。  
  
 このトピックのセクション:  
  
-   [テーブルのプロパティ](#bkmk_properties)  
  
-   [テーブル プロパティの設定を構成する](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> テーブルのプロパティ  
 **基本**  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|**接続名**|\<接続名 >|テーブルのデータ ソースに対する接続の名前。<br /><br /> 接続を編集するには、ボタンをクリックします。|  
|**[非表示]**|False|レポート クライアント フィールドの一覧で、テーブルを非表示にするかどうかを指定します。|  
|**パーティション**||テーブルのパーティションは、 **[プロパティ]** ウィンドウに表示できません。 パーティションを表示、作成、または編集するには、ボタンをクリックしてパーティション マネージャーを開きます。|  
|**ソース データ**||テーブルのソース データは、 **[プロパティ]** ウィンドウに表示できません。 ソース データを表示または編集するには、ボタンをクリックして [テーブルのプロパティの編集] ダイアログ ボックスを開きます。|  
|**テーブルの説明**||テーブルの説明文です。<br /><br /> [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]では、フィールド一覧のこのテーブルにエンド ユーザーがカーソルを重ねると、ツールヒントとしてこの説明が表示されます。|  
|**テーブル名**|\<フレンドリ名 >|テーブルの表示名を指定します。 テーブルのインポート ウィザードを使用してテーブルをインポートするとき、またはインポート後の任意の時点で、テーブル名を指定できます。 モデル内のテーブル名は、ソースに関連付けられているテーブルとは異なる場合があります。 テーブル表示名は、レポート クライアント アプリケーション フィールドのリストおよび [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のモデル データベース内に表示されます。|  
  
 **レポートのプロパティ**  
  
 詳細な説明とレポートのプロパティの構成については、次を参照してください。 [Power View レポート プロパティ](../../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md)です。  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|**既定のフィールド セット**|||  
|テーブルの動作|||  
  
##  <a name="bkmk_config_prop"></a> テーブル プロパティの設定を構成する  
  
1.  モデル デザイナーのデータ ビューでテーブル (タブ) をクリックするか、ダイアグラム ビューでテーブルのヘッダーをクリックします。  
  
2.  **[プロパティ]** ウィンドウで、プロパティをクリックして値を入力するか、ボタンをクリックして追加の構成オプションを選択します。  
  
  
