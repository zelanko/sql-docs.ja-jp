---
title: "パラメーター (ADO - WFC 構文) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Parameter collection [ADO], ADO/WFC syntax
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7006bc7073693cc70dcb8eebce1bd8998895a9e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="parameter-ado---wfc-syntax"></a>パラメーター (ADO - WFC 構文)
## <a name="package-commswfcdata"></a>パッケージ com.ms.wfc.data  
  
### <a name="constructor"></a>コンス トラクター  
  
```  
public Parameter()  
public Parameter(String name)  
public Parameter(String name, int type)  
public Parameter(String name, int type, int dir)  
public Parameter(String name, int type, int dir, int size)  
public Parameter(String name, int type, int dir, int size, Object value)  
```  
  
### <a name="methods"></a>メソッド  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
```  
  
### <a name="properties"></a>[プロパティ]  
  
```  
public int getAttributes()  
public void setAttributes(int attr)  
public int getDirection()  
public void setDirection(int dir)  
public String getName()  
public void setName(String name)  
public int getNumericScale()  
public void setNumericScale(int scale)  
public int getPrecision()  
public void setPrecision(int prec)  
public int getSize()  
public void setSize(int size)  
public int getType()  
public void setType(int type)  
public com.ms.com.Variant getValue()  
public void setValue(Object v)  
public AdoProperties getProperties()  
```  
  
## <a name="parameter-accessor-methods"></a>パラメーターのアクセサー メソッド  
 [値](../../../ado/reference/ado-api/value-property-ado.md)のプロパティ、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトを取得またはそのオブジェクトの内容を設定します。 コンテンツは、値を割り当てることができるオブジェクトの型といくつかのデータ型のいずれかのバリアント型として表されます。  
  
 ADO/WFC を実装して、**値**を持つプロパティ、 **getValue** 、バリアント型のオブジェクトを返すメソッド、および**setValue**を引数として VARIANT を受け取るメソッド。 バリアントは、Microsoft Visual Basic などの特定の言語に非常に効率的です。  
  
 加え、**値**プロパティ、ADO/WFC 提供*アクセサー*を取得および設定の内容を Java データ型を使用するメソッド**パラメーター**オブジェクト。 これらのメソッドのほとんどは、フォームの名前を持つ**取得***DataType*または**設定***DataType*です。  
  
 注目すべき 1 つの例外が発生: があるない**注意する必要**プロパティです。 代わりに、、 **isNull**フィールドが null かどうかを示すブール値を返します。  
  
```  
public boolean getBoolean()  
public void setBoolean(boolean v)  
public byte getByte()  
public void setByte(byte v)  
public double getDouble()  
public void setDouble(double v)  
public float getFloat()  
public void setFloat(float v)  
public int getInt()  
public void setInt(int v)  
public long getLong()  
public void setLong(long v)  
public short getShort()  
public void setShort(short v)  
public String getString()  
public void setString(String v)  
public boolean isNull()  
public void setNull()  
```  
  
## <a name="see-also"></a>参照  
 [パラメーター オブジェクト](../../../ado/reference/ado-api/parameter-object.md)

