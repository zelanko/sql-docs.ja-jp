---
title: "プロジェクトの設定 (変換) (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- conversion, options described
- Project Settings dialog box, Conversion
ms.assetid: bcebc635-c638-4ddb-924c-b9ccfef86388
caps.latest.revision: "16"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ce9b6bec50de99ba85561ec3a1679692ccb9bf6
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="project-settings-conversion-accesstosql"></a>プロジェクトの設定 (変換) (AccessToSQL)
変換のプロジェクト設定では、Access データベース オブジェクトからオブジェクトを変換する方法を構成できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースのオブジェクト。  
  
変換ウィンドウがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   使用して、**プロジェクト設定**ダイアログ ボックスを現在のプロジェクトの構成オプションを設定します。 変換の設定にアクセスする、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックし、左側のウィンドウの下部にある**変換**です。  
  
-   使用して、**プロジェクト設定の既定の**ダイアログ ボックスをすべてのプロジェクトの構成オプションを設定します。 変換の設定にアクセスする、**ツール**メニューの **プロジェクト設定の既定の**、対象の設定が表示する/から変更を必要な移行プロジェクトの種類を選択**移行のターゲット バージョン**ドロップダウンで、をクリックして**全般**クリックし、左側のウィンドウの下部にある**変換**です。  
  
## <a name="options"></a>オプション  
**Primary key を追加します。**  
新しい主キーを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Access のテーブルには、主キーまたは一意のインデックスがあるない場合は SQL Azure のテーブルです。  
  
-   **既定のモード**: False  
  
-   **オプティミスティック モード**: False  
  
-   **Full モード**: True  
  
SQL Azure に接続しているときは、既定では True です。**Timestamp 列を追加**  
必要な場合に、SSMA がタイムスタンプ値を作成するかどうかを指定します。  
  
-   **既定のモード**: Let SSMA の決定  
  
-   **オプティミスティック モード**: ことはありません  
  
-   **Full モード**: Let SSMA の決定  
  
**変換の評価レポートのデータ評価レポートを含める**  
評価レポートには、データの評価が含まれています。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: False  
  
-   **Full モード**: True  
  
**主キーには、null 許容の列が含まれている場合、メッセージの種類**  
SSMA を null 許容の列に主キーが見つかったときに出力ウィンドウに表示するメッセージ (警告、エラー、または何も行われません) の種類を指定します。  
  
-   **既定のモード**: 警告  
  
-   **オプティミスティック モード**: メッセージはありません  
  
-   **Full モード**: エラー  
  
**外部キー列がさまざまなサイズの場合、メッセージの種類**  
不正なテキスト外部キーが検出した場合に、SSMA が出力 ペインに表示されるメッセージ (警告、エラー、または何も行われません) の種類を指定します。  
  
-   **既定のモード**: 警告  
  
-   **オプティミスティック モード**: メッセージはありません  
  
-   **Full モード**: エラー  
  
**メモ列のインデックスが作成時に、メッセージの種類**  
SSMA を含むインデックスを見つけたときに出力ウィンドウに表示するメッセージ (警告、エラー、または何も行われません) の種類を指定します、 **memo**列です。  
  
-   **既定のモード**: 警告  
  
-   **オプティミスティック モード**: メッセージはありません  
  
-   **Full モード**: エラー  
  
**複雑なクエリでワイルドカードを使用する場合に警告する (\&#42;)**  
SELECT ステートメント内の列名がワイルドカード (*) の場合、出力ウィンドウおよび エラー一覧に警告を表示します。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: False  
  
-   **Full モード**: True  
  
**識別子の名前が変更されたときに警告する します。**  
SSMA により、オブジェクト識別子の名前が変更されたときに評価レポートでは出力ウィンドウにメッセージを表示します。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: False  
  
-   **Full モード**: True  
  
**識別子は引用符で囲む場合に警告する します。**  
オブジェクトの識別子名は SSMA で引用符で囲む場合は評価レポートと、出力ウィンドウのメッセージを表示します。 識別子を引用符で囲むと、名、キーワードまたは特殊文字を含む場合、必要があります。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: False  
  
-   **Full モード**: True  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイス Reference(Access)](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
