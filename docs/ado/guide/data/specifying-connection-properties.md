---
title: 接続のプロパティを指定する |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c198eb4c8118328d68b40deed4ab0e57ff561f9c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272663"
---
# <a name="specifying-connection-properties"></a>接続のプロパティを指定します。
によって指定された情報の大部分を指定することができます、[接続文字列](../../../ado/guide/data/creating-a-connection-string.md)のプロパティを設定して、**接続**接続を開く前にオブジェクト。 接続文字列がで説明したように、同じ効果を得ることがなど[接続文字列を作成する](../../../ado/guide/data/creating-a-connection-string.md)次のコードを使用しています。  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 接続が開いた後にのみ、DefaultDatabase が設定されています。  
  
> [!NOTE]
>  ADO では、セミコロンを含むパスワードを使用する必要がありますされません (「;」)、パスワードが単一引用符で囲まれている場合を除き、します。
