---
title: ObjectProxy (ADO-WFC 構文) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
author: rothja
ms.author: jroth
ms.openlocfilehash: ff9cd79b4ac787987ef44ea3f73cbd9fb102ae43
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762321"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - WFC 構文)
**Objectproxy**オブジェクトは、サーバーを表し、[そのオブジェクトの](../../../ado/reference/rds-api/dataspace-object-rds.md) **createObject**メソッドによって返されます。 ObjectProxy クラスには、1つのメソッドがあります。これ**は、サーバー**でメソッドを呼び出し、その呼び出しによって生成されたオブジェクトを返すことができます。  
  
 **パッケージ com.. wfc. データ**  
  
## <a name="methods"></a>メソッド  
  
### <a name="call-method-adowfc-syntax"></a>Call メソッド (ADO/WFC 構文)  
 ObjectProxy によって表されるサーバーでメソッドを呼び出します。 必要に応じて、メソッドの引数をオブジェクトの配列として渡すことができます。  
  
#### <a name="syntax"></a>構文  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>戻り値  
 オブジェクト  
 メソッドを呼び出した結果のオブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *ObjectProxy*  
 サーバーを表す**Objectproxy**オブジェクト。  
  
 *method*  
 サーバーで呼び出すメソッドの名前を格納している文字列。  
  
 *args*  
 任意。 サーバー上のメソッドの引数であるオブジェクトの配列。 Java のデータ型は、サーバーでの使用に適したデータ型に自動的に変換されます。
