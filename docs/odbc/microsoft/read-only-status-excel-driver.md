---
title: 読み取り専用の状態 (Excel ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d885124c9e4274d402bfa504b975f089d333af95
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="read-only-status-excel-driver"></a>読み取り専用の状態 (Excel ドライバー)
Microsoft Excel ドライバーを使用すると、データ ソース テーブルは既定では、読み取り専用で開かれ、一度に 1 つだけのユーザーが開くことができます。 テーブルでは、読み取り専用の状態がある、でもただし、アプリケーションを実行できます挿入と更新プログラム Microsoft Excel のテーブル。  
  
 アプリケーションは、Microsoft Excel ドライバーを使用して Microsoft Excel データでの名前を付けて保存コマンドを実行、アプリケーションを新しいテーブルを作成し、新しいテーブルに保存するデータを挿入します。 挿入は、テーブルに、追加で発生します。 テーブルの他の操作は実行されませんは閉じて再度開くまでです。 表が閉じられると、後続の挿入できるため実行できませんは、読み取り専用テーブル。  
  
 Excel ドライバーを使用する場合は、値を更新することが、Microsoft Excel スプレッドシートに基づいているため、更新プログラムとは見なされません、Excel ドライバーで正式にサポートされているテーブルから行を削除できません。
