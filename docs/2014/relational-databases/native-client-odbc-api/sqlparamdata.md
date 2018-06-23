---
title: SQLParamData |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd3fefeaa05f806650b58d1778658fda0ed63fa2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084775"
---
# <a name="sqlparamdata"></a>SQLParamData
  SQLParamData が返されるときに、 *ValuePtrPtr* 、テーブル値パラメーターに関連付けられた、アプリケーションと SQLPutData を呼び出す必要があります*StrLen_Or_Ind*です。 場合*StrLen_Or_Ind*が 0 より大きい値を持つアプリケーションが整っていることを意味、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を次のテーブル値パラメーター行のパラメーター データを収集します。 場合*StrLen_Or_Ind*値が 0 では、テーブル値パラメーターのデータの行を意味します。 詳細については、次を参照してください。[バインドおよび Data Transfer of Table-Valued パラメーターと列の値](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  