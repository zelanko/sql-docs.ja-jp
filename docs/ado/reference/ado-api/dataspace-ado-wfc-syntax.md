---
title: DataSpace (ADO - WFC 構文) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94a539fb2ba3285bd8bb5c3668879695598725a4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140106"
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO - WFC 構文)
**CreateObject**のメソッド、 **DataSpace**クラスをクライアント アプリケーションの要求を処理する、両方のビジネス オブジェクトを指定します (*progid*) との通信プロトコルサーバー (*接続*)。 **createObject**を返します、 [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md)サーバーを表すオブジェクト。  
  
## <a name="package-commswfcdata"></a>package com.ms.wfc.data  
  
### <a name="constructor"></a>コンストラクター  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>メソッド  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>プロパティ  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>参照  
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
