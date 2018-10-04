---
title: ADO Java クラス ラッパー |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 840d8a0e266a6f913a8a74ec1451bc6285fbb08b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729220"
---
# <a name="ado-java-class-wrappers"></a>ADO Java クラス ラッパー
このコードは、ADO のインスタンスを宣言して[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)クラス ラッパーと、コードの同じ行でそれを初期化します。 さらに、それぞれの引数の変数を宣言、[オープン](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッド、特に[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)と[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (Java をサポートしていないため、列挙型型の場合)。 開きし、閉じます、 **Recordset**オブジェクト。 Java が使用されていないオブジェクトの体系的な断続的なリリースを実行するときに解放するには、その変数をスケジュールするだけで Rs1 を NULL に設定します。  
  
```  
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>参照  
 [Microsoft SDK for Java を使用する](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
