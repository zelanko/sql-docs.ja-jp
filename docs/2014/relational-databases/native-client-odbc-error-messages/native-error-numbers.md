---
title: ネイティブエラー番号 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e7cd24a3eb1ccdeea1b6e6cbb97e2d0f222193f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63223497"
---
# <a name="native-error-numbers"></a>ネイティブ エラー番号
  データソースで発生したエラー (によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返される) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の場合、native Client ODBC ドライバーは、によっ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]て返されたネイティブエラー番号を返します。 ドライバーによって検出された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーの場合、NATIVE Client ODBC ドライバーは、ネイティブエラー番号0を返します。 ネイティブエラー番号の一覧の詳細については、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **master**データベースにある**sysmessages**システムテーブルの error 列を参照してください。  
  
 状態エラーコードの詳細については、「 [SQLSTATE &#40;ODBC エラーコード&#41;](sqlstate-odbc-error-codes.md)」を参照してください。 Net-Library から返されたエラーについては、ネイティブ エラー番号は基になるネットワーク ソフトウェアから返されます。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](handling-errors-and-messages.md)  
  
  
