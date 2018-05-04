---
title: インターフェイスの準拠レベル |Microsoft ドキュメント
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
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 2c470e54-0600-4b2b-b1f3-9885cb28a01a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 890684bf513b80cd484f7b15c75a04c38553513b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="interface-conformance-levels"></a>インターフェイスへの準拠レベル
平準化の目的は、どのような機能を利用して、ドライバーからアプリケーションに通知を開始します。 関数に基づく平準化方式は十分にこの目標を達成できません。 ODBC 3 です。*x*ドライバーは、所有する機能に基づいて分類されます。 関数をサポートする含めることができます、この機能をサポートします。によって返される情報の種類の記述子フィールド、ステートメント属性、"Y"の値をサポートするを含めることができますも**SQLGetInfo**のようにします。  
  
 インターフェイスへの準拠の仕様を簡略化は、ODBC は、次の 3 つの準拠レベルを定義します。 特定の準拠レベルを満たすためには、ドライバーはすべての準拠レベルの要件を満たす必要があります。 特定のレベルへの適合性では、すべての下位レベルに準拠して完全なを意味します。  
  
 準拠レベルは常に配分することに関してきちんと ODBC 関数の特定のリストのサポートに、次のセクションに記載されているサポートされる機能を指定します。 機能のサポートを提供するドライバーが特定の ODBC 関数呼び出しの一部またはすべてのフォームをサポートする必要があります (詳細については、次を参照してください[関数への準拠](../../../odbc/reference/develop-app/function-conformance.md))、特定の属性を設定 (を参照してください[属性への準拠。](../../../odbc/reference/develop-app/attribute-conformance.md))、および特定の記述子フィールド (を参照してください[記述子フィールドへの準拠](../../../odbc/reference/develop-app/descriptor-field-conformance.md))。  
  
 アプリケーションがデータ ソースへの接続を呼び出すことにより、ドライバーのインターフェイスへの準拠レベルを検出**SQLGetInfo** SQL_ODBC_INTERFACE_CONFORMANCE オプションを使用します。  
  
 ドライバーは、完全な一致を要求するレベルよりも機能の実装に解放されます。 アプリケーションが呼び出すことによってこのようなその他の機能を検出**SQLGetFunctions**を決定するどの ODBC 関数が存在) と**SQLGetInfo** (その他のさまざまな ODBC の機能のクエリを実行) します。  
  
 3 つの ODBC インターフェイスへの準拠レベル: コア、レベル 1 およびレベル 2 です。  
  
> [!NOTE]  
>  これらの準拠レベルは、ODBC 2 で同じ名前の ODBC API への準拠レベルよりも異なる要件を持つ *.x*です。 具体的には、ODBC 2 によって暗黙的にすべての機能 *.x* API への準拠レベル 1 は、コア インターフェイスへの準拠レベルの一部であるようになりました。 その結果、多くの ODBC ドライバーは、コア レベル インターフェイスへの準拠を報告する可能性があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [コア インターフェイスの適合性](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [レベル 1 インターフェイスの適合性](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [レベル 2 インターフェイスの適合性](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [関数の適合性](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [属性の適合性](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [記述子フィールドの適合性](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
