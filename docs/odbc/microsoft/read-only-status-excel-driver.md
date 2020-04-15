---
title: 読み取り専用ステータス (Excel ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb585d4712b6cac5e09b65ee8e13604763cd0164
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304023"
---
# <a name="read-only-status-excel-driver"></a>読み取り専用の状態 (Excel ドライバー)
Microsoft Excel ドライバを使用すると、データ ソース テーブルは既定で読み取り専用で開かれ、一度に 1 人のユーザーだけが開くことができます。 ただし、テーブルの状態が読み取り専用であっても、アプリケーションは Microsoft Excel テーブルの挿入と更新を実行できます。  
  
 アプリケーションが Microsoft Excel のドライバーを使用して Microsoft Excel データに対して [名前を付けて保存] コマンドを実行する場合、アプリケーションは新しいテーブルを作成し、新しいテーブルに保存するデータを挿入する必要があります。 テーブルに追加の結果を挿入します。 テーブルを閉じて再度開くまで、テーブルに対して他の操作を実行することはできません。 いったんテーブルを閉じると、そのテーブルが読み取り専用テーブルであるため、それ以降の挿入は実行できません。  
  
 Microsoft Excel ドライバを使用する場合は値を更新できますが、Excel スプレッドシートを基にテーブルから行を削除することはできないため、更新プログラムは Microsoft Excel ドライバで正式にサポートされているとは見なされません。
