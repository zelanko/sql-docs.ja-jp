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
manager: jroth
ms.openlocfilehash: ff7c5a2a2817fbe93d626ca7883107103edc58cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694717"
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile メソッド (ADO)
既存のファイルの内容を読み込み、 [Stream](../../../ado/reference/ado-api/stream-object-ado.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>パラメーター  
 *FileName*  
 A**文字列**に読み込まれるファイルの名前を含む値、 **Stream**します。 *ファイル名*任意の有効なパスと UNC 形式で名前に含めることができます。 指定したファイルが存在しない場合は、実行時エラーが発生します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、ローカル ファイルの内容を読み込むに使用できます、 **Stream**オブジェクト。 ローカル ファイルの内容をサーバーにアップロードするために使用できます。  
  
 **Stream**オブジェクトを呼び出す前に開いて既にある必要があります**LoadFromFile**します。 このメソッドのバインドを変更していない、 **Stream**オブジェクトは引き続き、URL で指定されたオブジェクトにバインドされますまたは**レコード**られて、 **Stream**もともと開かれます。  
  
 **LoadFromFile**の現在の内容を上書き、 **Stream**ファイルから読み取られるデータを持つオブジェクト。 既存のバイト、 **Stream**ファイルの内容で上書きされます。 次の既存の以前と残りのバイト、 [EOS](../../../ado/reference/ado-api/eos-property.md)によって作成された**LoadFromFile**、切り捨てられます。  
  
 呼び出しの後に**LoadFromFile**の先頭に、現在の位置が設定されている、 **Stream** ([位置](../../../ado/reference/ado-api/position-property-ado.md)は 0 です)。  
  
 2 バイトは、エンコード、ストリームの先頭に追加する場合があります、ため、ストリームのサイズが読み込み元のファイルのサイズが一致も一致しないです。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
