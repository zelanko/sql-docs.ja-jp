---
title: LoadFromFile メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce90b13a677246fb64462fbe691eb9e3efaa3c7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918268"
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile メソッド (ADO)
既存のファイルの内容を[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)に読み込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>パラメーター  
 */Db*  
 **ストリーム**に読み込むファイルの名前を含む**文字列**値です。 *FileName*には、任意の有効なパスと名前を UNC 形式で含めることができます。 指定したファイルが存在しない場合は、実行時エラーが発生します。  
  
## <a name="remarks"></a>解説  
 このメソッドを使用すると、ローカルファイルの内容を**ストリーム**オブジェクトに読み込むことができます。 これは、ローカルファイルの内容をサーバーにアップロードするために使用できます。  
  
 **LoadFromFile**を呼び出す前に、**ストリーム**オブジェクトが既に開かれている必要があります。 このメソッドは、**ストリーム**オブジェクトのバインディングを変更しません。それでも、**ストリーム**が最初に開かれた URL または**レコード**で指定されたオブジェクトにバインドされます。  
  
 **LoadFromFile**は、ファイルから読み取ったデータを使用して、**ストリーム**オブジェクトの現在の内容を上書きします。 **ストリーム**内の既存のバイトは、ファイルの内容によって上書きされます。 **LoadFromFile**によって作成された[EOS](../../../ado/reference/ado-api/eos-property.md)の後にある既存のバイトと残りのバイトは、切り捨てられます。  
  
 **LoadFromFile**の呼び出しの後、現在の位置は**ストリーム**の先頭に設定されます ([position](../../../ado/reference/ado-api/position-property-ado.md)は 0)。  
  
 エンコードのためにストリームの先頭に2バイトが追加される可能性があるため、ストリームのサイズが、読み込み元のファイルのサイズと完全に一致しない場合があります。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
