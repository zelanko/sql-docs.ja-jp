---
title: "自動生成、IPD |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d637ddfebc0563ed2591740498d519f91e34321e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="automatic-population-of-the-ipd"></a>IPD の自動設定
一部のドライバーでは、パラメーター化クエリを準備した後、IPD のフィールドを設定できます。 記述子フィールドには、データ型、有効桁数、小数点以下桁数、およびその他の特性を含め、パラメーターに関する情報が自動的に設定されます。 これはサポートに相当**SQLDescribeParam**です。 この情報は、アプリケーションが認識していないパラメーターを使用してアドホック クエリが行われる場合など、検出するには、他の方法があるないときをアプリケーションに特に有用です。  
  
 アプリケーションでは、ドライバーで呼び出すことによって自動作成をサポートするかどうかを判断**SQLGetConnectAttr**で、*属性*SQL_ATTR_AUTO_IPD のです。 SQL_TRUE が返される場合は、ドライバーではサポートし、アプリケーションが SQL_TRUE に SQL_ATTR_ENABLE_AUTO_IPD ステートメント属性を設定して有効ことができます。  
  
 呼び出しでパラメーター マーカーを含む SQL ステートメントが準備した後に、ドライバーが、IPD のフィールドを設定します自動作成はサポートされているし、有効になっている、 **SQLPrepare**です。 アプリケーションが呼び出すことでこの情報を取得できます**SQLGetDescField**または**SQLGetDescRec**、または**SQLDescribeParam**です。 パラメーターに最も適切なアプリケーション バッファーをバインドするか、データ変換を指定する、アプリケーションは、情報を使用できます。  
  
 IPD の自動設定には、パフォーマンスの低下を生じる可能性があります。 アプリケーションをオフに SQL_FALSE (既定値) に SQL_ATTR_ENABLE_AUTO_IPD ステートメント属性をリセットすることで。
