---
title: スクロール可能なカーソルとトランザクションの分離 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 68517f733dcb10f75669341bdef861b035b79a72
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>スクロール可能なカーソルとトランザクションの分離
次の表は、変化の見え方を規定する要因を一覧表示します。  
  
|によって行われた変更:|可視性によって異なります。|  
|----------------------|----------------------------|  
|カーソル|カーソルの種類、カーソルの実装|  
|同じトランザクション内で他のステートメント|カーソルの種類|  
|他のトランザクション内のステートメント|カーソルの種類、トランザクション分離レベル|  
  
 これらの要因は、次の図に表示されます。  
  
 ![変化の見え方を規定する要因](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 次の表は、単独で、独自のトランザクションで他の操作によって、および他のトランザクションによって加えられた変更を検出する各カーソルの種類の機能をまとめたものです。 後者の変更の可視性は、カーソルの種類と、カーソルを含むトランザクションの分離レベルによって異なります。  
  
|カーソル type\action|Self|自分が所有します。<br /><br /> Txn|他<br /><br /> Txn<br /><br /> (RU[a])|他<br /><br /> Txn<br /><br /> (RC[a])|他<br /><br /> Txn<br /><br /> (RR[a])|他<br /><br /> Txn<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|静的|||||||  
|Insert|おそらく [b]|いいえ|いいえ|いいえ|いいえ|いいえ|  
|Update|おそらく [b]|いいえ|いいえ|いいえ|いいえ|いいえ|  
|Del|おそらく [b]|いいえ|いいえ|いいえ|いいえ|いいえ|  
|キーセット ドリブン|||||||  
|Insert|おそらく [b]|いいえ|いいえ|いいえ|いいえ|いいえ|  
|Update|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|いいえ|いいえ|  
|Del|おそらく [b]|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|いいえ|いいえ|  
|動的|||||||  
|Insert|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|いいえ|  
|Update|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|いいえ|いいえ|  
|Del|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|いいえ|いいえ|  
  
 [a] かっこで囲まれた文字が、カーソルを含むトランザクションの分離レベルを示します(変更が行われた場所)、その他のトランザクションの分離レベルは無効です。  
  
 コミットされていない RU: 読み取り  
  
 コミット RC: 読み取り  
  
 RR: Repeatable read  
  
 %S: シリアル化可能です  
  
 [b] は、カーソルの実装に依存します。 SQL_STATIC_SENSITIVITY オプションによって、カーソルがこのような変更を検出するかどうかは報告**SQLGetInfo**です。
