---
title: "LoadFromFile メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 071ba2d6a2aa5af96af07274455a7495a9650dea
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile メソッド (ADO)
既存のファイルの内容を読み込みます、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>パラメーター  
 *FileName*  
 A**文字列**に読み込まれるファイルの名前を表す値、**ストリーム**です。 *FileName*任意の有効なパスと UNC 形式で名前を含めることができます。 指定したファイルが存在しない場合は、実行時エラーが発生します。  
  
## <a name="remarks"></a>解説  
 このメソッドにローカル ファイルの内容を読み込みに使用できます、**ストリーム**オブジェクト。 ローカル ファイルの内容をサーバーにアップロードするために使用できます。  
  
 **ストリーム**オブジェクトの呼び出しの前に開いているが既にあります**LoadFromFile**です。 このメソッドのバインドを変更していない、**ストリーム**オブジェクトはまだ URL で指定されたオブジェクトにバインドされますまたは**レコード**を**ストリーム**もともと開かれます。  
  
 **LoadFromFile**の現在の内容を上書き、**ストリーム**ファイルから読み取られるデータを持つオブジェクト。 既存のバイト、**ストリーム**ファイルの内容で上書きされます。 次の既存の前と残りのバイト、 [EOS](../../../ado/reference/ado-api/eos-property.md)によって作成された**LoadFromFile**、切り捨てられます。  
  
 呼び出しの後に**LoadFromFile**の先頭に、現在の位置が設定されている、**ストリーム**([位置](../../../ado/reference/ado-api/position-property-ado.md)は 0) です。  
  
 エンコードするためのストリームの先頭には、2 バイトを追加することがあります、ため、ストリームのサイズが完全に一致しないの読み込み元のファイルのサイズ。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
