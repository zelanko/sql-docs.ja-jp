---
title: "Java クラス ラッパーを ADO |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 08cbd288ba9f64816ae0c8fd62c18171967c4d0d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="ado-java-class-wrappers"></a>ADO Java クラスのラッパー
このコードは、ADO のインスタンスを宣言して[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)クラス ラッパーして初期化し、すべてのコードの同じ行にします。 さらに、引数は、の各変数を宣言、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッド、特に[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)と[カーソル](../../../ado/reference/ado-api/cursortype-property-ado.md)(Java はサポートされていない列挙型。型の場合)。 これの開閉、**レコード セット**オブジェクト。 Java が使用されていないオブジェクトの体系的な断続的なリリースを実行するときに解放するには、その変数をスケジュールだけ Rs1 を NULL に設定します。  
  
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
 [Java の Microsoft SDK を使用します。](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)

