---
title: SQLParamData |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 912d4b0a6f6a7565d62cb3f81f14ee4c99234974
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705932"
---
# <a name="sqlparamdata"></a>SQLParamData
  SQLParamData が、テーブル値パラメーターに関連付けられた*Valueptrptr*を返す場合、アプリケーションは*StrLen_Or_Ind*を使用して sqlparamdata を呼び出す必要があります。 *StrLen_Or_Ind*の値が0より大きい場合は、アプリケーションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 次のテーブル値パラメーター行のパラメーターデータを収集する準備ができていることを意味します。 *StrLen_Or_Ind*の値が0の場合は、テーブル値パラメーターのデータ行がこれ以上存在しないことを意味します。 詳細については、「[テーブル値パラメーターと列値のバインドとデータ転送](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
