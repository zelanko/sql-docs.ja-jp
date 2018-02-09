---
title: "ObjectProxy (ADO - WFC 構文) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 19884e98de3a6ed8070dcd30d3965c7ad9e77a4c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - WFC 構文)
**ObjectProxy**オブジェクトは、サーバーを表し、によって返される、 **createObject**のメソッド、 [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクト。 ObjectProxy クラスが 1 つのメソッド、**呼び出す**サーバー上のメソッドを呼び出すし、呼び出しの結果オブジェクトを返すことができます。  
  
 **package com.ms.wfc.data**  
  
## <a name="methods"></a>メソッド  
  
### <a name="call-method-adowfc-syntax"></a>Call メソッド (ADO/WFC 構文)  
 ObjectProxy によって表されるサーバー上のメソッドを呼び出します。 必要に応じて、メソッドの引数は、オブジェクトの配列として渡すことができます。  
  
#### <a name="syntax"></a>構文  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>返します。  
 オブジェクト  
 メソッドを呼び出し、結果のオブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *ObjectProxy*  
 **ObjectProxy**サーバーを表すオブジェクト。  
  
 *method*  
 サーバーで呼び出すメソッドの名前を含む文字列。  
  
 *args*  
 省略可。 サーバー上のメソッドの引数であるオブジェクトの配列。 Java データ型は、サーバー上の使用に適したデータ型に自動的に変換されます。
