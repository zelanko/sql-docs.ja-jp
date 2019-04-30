---
title: 接続プロパティの指定 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 885d201736adb3cd16efbea4f3907cd0aa324128
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062828"
---
# <a name="specifying-connection-properties"></a>接続プロパティの指定
指定された情報の多くを指定することができます、[接続文字列](../../../ado/guide/data/creating-a-connection-string.md)のプロパティを設定して、**接続**接続を開く前にオブジェクト。 接続文字列で説明したように、同じ効果を得ることができますなど[接続文字列を作成する](../../../ado/guide/data/creating-a-connection-string.md)次のコードを使用します。  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase は、接続を開いた後にのみ設定されます。  
  
> [!NOTE]
>  ADO では、セミコロンを含むパスワードを使用する必要がありますされません (「;」)、パスワードが単一引用符で囲まれている場合を除き、します。
