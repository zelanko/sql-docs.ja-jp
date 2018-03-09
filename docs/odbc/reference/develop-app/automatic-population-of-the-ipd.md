---
title: "自動生成、IPD |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be483c04101007383a4672701ac2cdfefbade862
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="automatic-population-of-the-ipd"></a>IPD の自動設定
一部のドライバーでは、パラメーター化クエリを準備した後、IPD のフィールドを設定できます。 記述子フィールドには、データ型、有効桁数、小数点以下桁数、およびその他の特性を含め、パラメーターに関する情報が自動的に設定されます。 これはサポートに相当**SQLDescribeParam**です。 この情報は、アプリケーションが認識していないパラメーターを使用してアドホック クエリが行われる場合など、検出するには、他の方法があるないときをアプリケーションに特に有用です。  
  
 アプリケーションでは、ドライバーで呼び出すことによって自動作成をサポートするかどうかを判断**SQLGetConnectAttr**で、*属性*SQL_ATTR_AUTO_IPD のです。 SQL_TRUE が返される場合は、ドライバーではサポートし、アプリケーションが SQL_TRUE に SQL_ATTR_ENABLE_AUTO_IPD ステートメント属性を設定して有効ことができます。  
  
 呼び出しでパラメーター マーカーを含む SQL ステートメントが準備した後に、ドライバーが、IPD のフィールドを設定します自動作成はサポートされているし、有効になっている、 **SQLPrepare**です。 アプリケーションが呼び出すことでこの情報を取得できます**SQLGetDescField**または**SQLGetDescRec**、または**SQLDescribeParam**です。 パラメーターに最も適切なアプリケーション バッファーをバインドするか、データ変換を指定する、アプリケーションは、情報を使用できます。  
  
 IPD の自動設定には、パフォーマンスの低下を生じる可能性があります。 アプリケーションをオフに SQL_FALSE (既定値) に SQL_ATTR_ENABLE_AUTO_IPD ステートメント属性をリセットすることで。
