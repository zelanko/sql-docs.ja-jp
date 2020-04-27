---
title: SaveToFile メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2e56178ad306d5b39c2445c391c3bbabe4fc424
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917034"
---
# <a name="savetofile-method"></a>SaveToFile メソッド
[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)のバイナリコンテンツをファイルに保存します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>パラメーター  
 *FileName*  
 **ストリーム**の内容の保存先となるファイルの完全修飾名を含む**文字列**値です。 任意の有効なローカルの場所、または UNC 値を使用してアクセスできる任意の場所に保存できます。  
  
 *System.xml.linq.saveoptions>*  
 新しいファイルがまだ存在しない場合に、新しいファイルを**SaveToFile**によって作成するかどうかを指定する[Saveoptionsenum](../../../ado/reference/ado-api/saveoptionsenum.md)値。 既定値は**adSaveCreateNotExists**です。 これらのオプションを使用すると、指定したファイルが存在しない場合にエラーが発生するように指定できます。 また、 **SaveToFile**が既存のファイルの現在の内容を上書きするように指定することもできます。  
  
> [!NOTE]
>  既存のファイルを上書きする場合 ( **adSaveCreateOverwrite**が設定されている場合)、 **SaveToFile**は新しい[EOS](../../../ado/reference/ado-api/eos-property.md)の後にある元の既存のファイルからすべてのバイトを切り捨てます。  
  
## <a name="remarks"></a>Remarks  
 **SaveToFile**は、**ストリーム**オブジェクトの内容をローカルファイルにコピーするために使用できます。 **ストリーム**オブジェクトの内容またはプロパティに変更はありません。 **ストリーム**オブジェクトは、 **SaveToFile**を呼び出す前に開いている必要があります。  
  
 このメソッドは、**ストリーム**オブジェクトと基になるソースとの関連付けを変更しません。 **ストリーム**オブジェクトは、開いたときにソースであった元の URL または**レコード**と関連付けられたままになります。  
  
 **SaveToFile**操作の後、ストリーム内の現在位置 ([位置](../../../ado/reference/ado-api/position-property-ado.md)) がストリームの先頭 (0) に設定されます。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
