---
title: ADO Java クラスラッパー |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70486a27cfbe5c977d371906da89563059685093
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67927006"
---
# <a name="ado-java-class-wrappers"></a>ADO Java クラス ラッパー
このコードは、ADO[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)クラスラッパーのインスタンスを宣言し、それをすべて同じコード行で初期化します。 さらに、 [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドの各引数の変数を宣言します。これは特に、 [LockType](../../../ado/reference/ado-api/locktype-property-ado.md)と[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (Java では列挙型をサポートしていないため) です。 **レコードセット**オブジェクトが開き、閉じます。 Rs1 を NULL に設定すると、Java が使用されていないオブジェクトの体系的かつ断続的なリリースを実行するときに、その変数が解放されるようにスケジュールされます。  
  
```java
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>参照  
 [Microsoft SDK for Java を使用する](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
