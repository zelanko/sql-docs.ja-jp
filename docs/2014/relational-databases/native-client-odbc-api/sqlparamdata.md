---
title: SQLParamData |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da50163b90d4a871c2524e1723797474386be8f6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046667"
---
# <a name="sqlparamdata"></a>SQLParamData
  SQLParamData が返されるときに、 *ValuePtrPtr*テーブル値パラメーターでは、関連付けられているアプリケーションと SQLPutData を呼び出す必要があります*StrLen_Or_Ind*します。 場合*StrLen_Or_Ind* 、0 より大きい値を持つアプリケーションが整ったことになります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client を次のテーブル値パラメーター行のパラメーターのデータを収集します。 場合*StrLen_Or_Ind*の値を持つ 0 はテーブル値パラメーターのデータの行を意味します。 詳細については、次を参照してください。[バインドと Data Transfer of Table-Valued パラメーターおよび列の値](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)します。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
