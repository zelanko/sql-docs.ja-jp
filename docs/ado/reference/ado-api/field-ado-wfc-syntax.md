---
title: フィールド (ADO - WFC 構文) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Field collection [ADO], ADO/WFC syntax
ms.assetid: 7e01cb24-2338-4f92-ad46-8d97248e1a4d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0786b7318ccdd2efb490537dce3987800c9c3632
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="field-ado---wfc-syntax"></a>フィールド (ADO - WFC 構文)
## <a name="package-commswfcdata"></a>パッケージ com.ms.wfc.data  
  
### <a name="methods"></a>メソッド  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
public byte[] getByteChunk(int len)  
public char[] getCharChunk(int len)  
public String getStringChunk(int len)  
```  
  
### <a name="properties"></a>プロパティ  
  
```  
public int getActualSize()  
public int getAttributes()  
public void setAttributes(int pl)  
public com.ms.com.IUnknown getDataFormat()  
public void setDataFormat(com.ms.com.IUnknown format)  
```  
  
 (詳細については、com.ms.wfc.data.IDataFormat インターフェイスのドキュメントを参照してください)。  
  
```  
public int getDefinedSize()  
public void setDefinedSize(int pl)  
public String getName()  
public int getNumericScale()  
public void setNumericScale(byte pbNumericScale)  
public Variant getOriginalValue()  
public int getPrecision()  
public void setPrecision(byte pbPrecision)  
public int getType()  
public void setType(int pDataType)  
public Variant getUnderlyingValue()  
public Variant getValue()  
public void setValue(Variant value)  
public AdoProperties getProperties()  
```  
  
### <a name="field-accessor-methods"></a>フィールドのアクセサー メソッド  
 [値](../../../ado/reference/ado-api/value-property-ado.md)のプロパティ、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトを取得またはそのオブジェクトの内容を設定します。 コンテンツは、値を割り当てることができるオブジェクトの型といくつかのデータ型のいずれかのバリアント型として表されます。  
  
 ADO/WFC を実装して、**値**を持つプロパティ、 **getValue** 、バリアント型のオブジェクトを返すメソッド、および**setValue**を引数として VARIANT を受け取るメソッド。 バリアントは、Microsoft Visual Basic などの特定の言語に非常に効率的です。  
  
 加え、**値**プロパティ、ADO/WFC 提供*アクセサー*を取得および設定の内容を Java データ型を使用するメソッド**フィールド**オブジェクト。 これらのメソッドのほとんどは、フォームの名前を持つ **取得 * * * DataType*または **設定 * * * DataType*です。  
  
 2 つの注目すべき例外があります: のいずれか、 **getObject**メソッドは、指定したクラスに強制型変換オブジェクトを返します。 ない**注意する必要**プロパティです。 代わりに、、 **isNull**フィールドが null かどうかを示すブール値を返します。  
  
```  
public native boolean getBoolean();  
public void setBoolean(boolean v)  
public native byte getByte();  
public void setByte(byte v)  
public native byte[] getBytes();  
public void setBytes(byte[] v)  
public native double getDouble();  
public void setDouble(double v)  
public native float getFloat();  
public void setFloat(float v)  
public native int getInt();  
public void setInt(int v)  
public native long getLong();  
public void setLong(long v)  
public native short getShort();  
public void setShort(short v)  
public native String getString();  
public void setString(String v)  
public native boolean isNull();  
public void setNull()  
public Object getObject()  
public Object getObject(Class c)  
public void setObject(Object value)  
```  
  
## <a name="see-also"></a>参照  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)
