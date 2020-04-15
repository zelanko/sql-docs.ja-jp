---
title: インターフェイス準拠レベル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 2c470e54-0600-4b2b-b1f3-9885cb28a01a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fff555324746fcb92641126ddf11ea91ce5e3f89
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304602"
---
# <a name="interface-conformance-levels"></a>インターフェイスの適合性レベル
平準化の目的は、ドライバーから、アプリケーションに利用可能な機能を通知することです。 関数に基づく平準化スキームでは、この目標を十分に達成できません。 ODBC 3 で。*x、* ドライバは、彼らが所有する機能に基づいて分類されます。 機能のサポートには、関数のサポートが含まれます。また、記述子フィールド、ステートメント属性 **、SQLGetInfo**によって返される情報型の "Y" 値のサポートを含めることもできます。  
  
 インターフェイスの準拠の仕様を簡略化するために、ODBC は 3 つの準拠レベルを定義します。 特定の準拠レベルを満たすには、ドライバーがその準拠レベルのすべての要件を満たす必要があります。 特定のレベルとの適合性は、すべての下位レベルと完全に適合していることを意味します。  
  
 準拠レベルは、ODBC 関数の特定のリストのサポートに必ずしもきちんと分割されるわけではありませんが、次のセクションに示すようにサポートされている機能を指定します。 機能をサポートするには、ドライバーが特定の ODBC 関数に対する呼び出しの一部またはすべての形式をサポートする必要があります (詳細については、「[関数の一致」](../../../odbc/reference/develop-app/function-conformance.md)を参照してください)、特定の属性を設定する ([属性の一致](../../../odbc/reference/develop-app/attribute-conformance.md)を参照)、および特定の記述子フィールド ([記述子フィールドの一致を](../../../odbc/reference/develop-app/descriptor-field-conformance.md)参照)。  
  
 アプリケーションは、データ ソースに接続し、SQL_ODBC_INTERFACE_CONFORMANCE オプションを使用して**SQLGetInfo**を呼び出すことによって、ドライバーのインターフェイスの準拠レベルを検出します。  
  
 ドライバーは、完全な準拠を要求するレベルを超える機能を実装する自由です。 アプリケーションは **、SQLGetFunctions** (存在する ODBC 関数を確認する) と**SQLGetInfo** (他の各種 ODBC 機能を照会する) を呼び出すことによって、このような追加機能を検出します。  
  
 ODBC インターフェイスの準拠レベルには、コア、レベル 1、およびレベル 2 の 3 つがあります。  
  
> [!NOTE]
>  これらの準拠レベルは、ODBC 2 *.x*の同じ名前の ODBC API 準拠レベルとは異なる要件を持ちます。 特に、ODBC 2 *.x* API 準拠レベル 1 で示されるすべての機能は、コア インターフェイス準拠レベルの一部になりました。 その結果、多くの ODBC ドライバがコア レベル のインターフェイスの準拠を報告する場合があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [コア インターフェイスの適合性](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [レベル 1 インターフェイスの適合性](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [レベル 2 インターフェイスの適合性](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [関数の適合性](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [属性の適合性](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [記述子フィールドの適合性](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
