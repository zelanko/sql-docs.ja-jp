---
title: ネイティブ エラー番号 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 394d349e9edab24005244b8442f16623672c93a8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407121"
---
# <a name="native-error-numbers"></a>ネイティブ エラー番号
  データ ソースで発生するエラー (によって返される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーによって返されたネイティブ エラー番号を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 ドライバーで検出されたエラー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、ネイティブ エラー番号は 0 を返します。 ネイティブ エラー番号の一覧については、のエラー列を参照して、 **sysmessages**システム テーブルに、**マスター**データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 状態エラー コードについては、次を参照してください。 [SQLSTATE &#40;ODBC エラー コード&#41;](sqlstate-odbc-error-codes.md)します。 Net-Library から返されたエラーについては、ネイティブ エラー番号は基になるネットワーク ソフトウェアから返されます。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](handling-errors-and-messages.md)  
  
  
