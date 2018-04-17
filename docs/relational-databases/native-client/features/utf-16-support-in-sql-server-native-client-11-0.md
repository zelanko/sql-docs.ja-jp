---
title: SQL Server Native Client 11.0 での utf-16 のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|features
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6bc1b14d63aa95ecdfe6cfaa8585533e163cd971
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>SQL Server Native Client 11.0 での UTF-16 のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]以降、列の結果または出力パラメーターをバインドするときに固定長バッファーを指定した場合、ターミネータ文字の前にバッファーに書き込まれる **wchar** 文字がサロゲート ペアの上位サロゲート コード ポイントである場合、および次の **wchar** 文字が下位サロゲート コード ポイントである場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はバッファーに上位サロゲート コード ポイントを追加しません。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
