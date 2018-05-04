---
title: オプティミスティック同時実行制御 |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- optimistic concurrency [ODBC]
ms.assetid: 9d71e09e-bc68-4c1f-9229-ed2a7be7d324
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01076f3f9167af8b67153abf9f3458a63bed1bf3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="optimistic-concurrency"></a>オプティミスティック同時実行制御
*オプティミスティック同時実行制御*というオプティミスティックな仮定からその名前を取得するトランザクション間で競合が発生することはほとんどありません以外の場合は、競合が発生している別のトランザクションを更新または読み取られるまでの間のデータの行を削除すると言われますによって、現在のトランザクションと、時刻が更新または削除します。 は、その逆の*ペシミスティック同時実行性、*をロックするかをアプリケーションの開発者と見なすこのような競合がある一般的にします。  
  
 オプティミスティック同時実行性、行の左側を更新または削除して、時刻になるまでのロックを解除します。 その時点では、行が再度読み取るし、チェックするかどうかは変更されている最後の読み取り以降を参照してください。 行変更した後は更新または削除は失敗して再試行する必要があります。  
  
 行が変更されたかどうかを判断するのには、その新しいバージョンが、行のキャッシュされたバージョン照らし合わせてチェックされます。 このチェックは、SQL Server、または行の各列の値のタイムスタンプ列など、行のバージョンに基づくことができます。 多くの dbms では、行のバージョンをサポートしていません。  
  
 データ ソースまたはアプリケーションによっては、オプティミスティック同時実行制御を実装できます。 どちらの場合、アプリケーションが Read Committed; などの低いトランザクション分離レベルを使用します。高いレベルを使用してオプティミスティック同時実行制御によって得られる増加の同時実行を否定します。  
  
 オプティミスティック同時実行制御は、データ ソースによって実装されている場合、アプリケーションは、SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES を SQL_ATTR_CONCURRENCY ステートメント属性を設定します。 更新または行の削除、位置指定更新または削除ステートメントの呼び出しを実行**SQLSetPos**場合、ドライバーまたはデータ ソースは SQLSTATE 01001 (カーソル操作 conflict) を返します、ペシミスティック同時実行制御; と同様、更新または削除は、競合しているため失敗します。  
  
 アプリケーション自体では、オプティミスティック同時実行制御を実装する場合は、行を読み取る SQL_CONCUR_READ_ONLY を SQL_ATTR_CONCURRENCY ステートメント属性を設定します。 行のバージョンを比較し、行バージョン列が認識していない場合は呼び出し**SQLSpecialColumns**この列の名前を決定する SQL_ROWVER オプションを使用します。  
  
 アプリケーションを更新または SQL_CONCUR_LOCK (書き込みアクセスするために、行) を実行して同時実行を増やすことで、行を削除、**更新**または**削除**ステートメントを**場所**バージョンを指定または行の値を句は、アプリケーションで読み取られるときに必要があります。 その後、行が変更された場合、ステートメントは失敗します。 場合、**場所**句が行を一意に識別されない、ステートメント可能性がありますも更新、またはその他の行を削除以外の場合は行のバージョンでは、行、常に一意に識別する、行の値は行を一意に識別、主キーが含まれる場合にのみです。
