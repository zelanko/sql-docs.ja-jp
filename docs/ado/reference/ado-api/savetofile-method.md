---
title: "SaveToFile メソッド |Microsoft ドキュメント"
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
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64fa2093400ac9c003397659be3d9d6f4251eee2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="savetofile-method"></a>SaveToFile メソッド
バイナリの内容を保存、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)をファイルにします。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>パラメーター  
 *FileName*  
 A**文字列**先のファイルの完全修飾名を表す値の内容、**ストリーム**は保存されます。 有効なローカルの場所に保存できますか、UNC 値を使用してへのアクセスが任意の場所。  
  
 *SaveOptions*  
 A [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)によって新しいファイルを作成するかどうかを指定する値**SaveToFile**が既に存在しない場合、します。 既定値は**adSaveCreateNotExists**です。 これらのオプションで指定されたファイルが存在しない場合にエラーが発生したことを指定できます。 指定することもできます**SaveToFile**既存のファイルの現在の内容が上書きされます。  
  
> [!NOTE]
>  既存のファイルを上書きした場合 (ときに**adSaveCreateOverwrite**設定されている)、 **SaveToFile**新しい後に続く元の既存のファイルからバイトを切り捨てます[EOS](../../../ado/reference/ado-api/eos-property.md)です。  
  
## <a name="remarks"></a>解説  
 **SaveToFile**の内容をコピーするために使用する可能性があります、**ストリーム**オブジェクトをローカル ファイルにします。 コンテンツまたはのプロパティの変更はありません、**ストリーム**オブジェクト。 **ストリーム**オブジェクトを呼び出す前に開く必要があります**SaveToFile**です。  
  
 このメソッドの関連付けを変更していない、**ストリーム**基になるソース オブジェクト。 **ストリーム**オブジェクトが元の URL に関連付けられるまだまたは**レコード**開かれたときに、ソースとなった。  
  
 後に、 **SaveToFile**操作、現在の位置 ([位置](../../../ado/reference/ado-api/position-property-ado.md))、ストリームでは (0) のストリームの先頭に設定します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
