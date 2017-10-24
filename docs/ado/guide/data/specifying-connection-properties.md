---
title: "接続のプロパティを指定する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 49399204f536d32321d46f1a8acba0ae435583c5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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

