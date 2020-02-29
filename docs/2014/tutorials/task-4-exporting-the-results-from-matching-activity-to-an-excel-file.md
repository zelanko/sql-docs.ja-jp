---
title: 'タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4ed1d29af328a162eafadb1ce7a160c262bdcba3
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177250"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする
  ここでは、照合アクティビティから Excel ファイルに結果をエクスポートします。

1.  [**エクスポート**] ページで、**変換先の種類**として [ **Excel ファイル**] を選択します。

2.  **サバイバーシップ Results**オプションを選択します。 サバイバーシッププロセスでは、選択した**サバイバーシップルール**に基づいて、各クラスターの保持レコードが DQS によって決定されます。

3.  [**参照**] をクリックし、出力ファイルを保存するフォルダーに移動します。

4.  名前として「**クレンジングして一致する仕入先 .xls** 」と入力し、[**開く**] をクリックします。

5.  **サバイバーシップルール**に [**ピボットレコード**が選択されていることを確認します。 このオプションを選択すると、各クラスターのピボット レコードがクラスターからの出力に選択されます。 サバイバーシップ ルールの他のオプションは次のとおりです。

    1.  **最も完全なレコード:** 保持 record は、入力されたフィールドの数が最も多いレコードです。

    2.  **最長のレコード:** 保持 record は、ソースフィールド内の用語の数が最も多いレコードです。

    3.  **最も完全で最長のレコード:** 保持 record は、入力されたフィールドの数が最も多く、各フィールドに含まれる用語の数が最も多いレコードです。

     ![照合の結果ページのエクスポート](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "照合の結果ページのエクスポート")

6.  [**エクスポート**] をクリックして、結果を Excel ファイルにエクスポートします。

7.  [**閉じる**] をクリックして、[**一致するエクスポート**] ダイアログボックスを閉じます。

8.  [**完了**] をクリックして照合アクティビティを終了します。

9. クレンジングされて**一致する仕入先 .xlsx**ファイルを開き、重複がないことを確認します ([仕入先])。

 これで、仕入先データは重複項目を削除するためにクレンジングおよび照合されました。

## <a name="next-step"></a>次のステップ
 [レッスン 4: MDS に仕入先データを格納する](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)


