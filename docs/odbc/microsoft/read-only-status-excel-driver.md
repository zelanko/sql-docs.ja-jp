---
title: 読み取り専用の状態 (Excel ドライバー) |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304023"
---
# <a name="read-only-status-excel-driver"></a>読み取り専用の状態 (Excel ドライバー)
Microsoft Excel ドライバーを使用すると、データソーステーブルは既定では読み取り専用として開かれ、一度に1人のユーザーのみが開くことができます。 ただし、テーブルに読み取り専用の状態がある場合でも、アプリケーションは Microsoft Excel テーブルの挿入と更新を実行できます。  
  
 アプリケーションが microsoft excel ドライバーを使用して Microsoft Excel データに対して [名前を付けて保存] コマンドを実行する場合、アプリケーションは新しいテーブルを作成し、新しいテーブルに保存するデータを挿入する必要があります。 結果をテーブルに追加します。 テーブルを閉じて再度開くまで、テーブルに対して他の操作を実行することはできません。 テーブルを閉じた後は、テーブルが読み取り専用テーブルであるため、後続の挿入を実行することはできません。  
  
 Microsoft excel driver を使用する場合、値を更新することはできますが、Microsoft Excel スプレッドシートに基づくテーブルから行を削除することはできないため、更新プログラムは Microsoft Excel ドライバーで正式にサポートされているとは見なされません。
