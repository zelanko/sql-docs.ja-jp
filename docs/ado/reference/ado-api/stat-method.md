---
title: Stat メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0538a3afae1e4c0bf4159d8ef6a42872f21ff6ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916868"
---
# <a name="stat-method"></a>Stat メソッド
[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトに関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>戻り値  
 操作の状態を示す**Long 型**の値。  
  
#### <a name="parameters"></a>パラメーター  
 *StatStg*  
 ストリームに関する情報が格納される STATSTG 構造体。 ADO ストリームオブジェクトによって使用される**Stat**メソッドの実装では、構造体のすべてのフィールドが格納されるわけではありません。  
  
 *StatFlag*  
 このメソッドが STATSTG 構造体の一部のメンバーを返さないことを指定します。これにより、メモリ割り当て操作が保存されます。 値は STATFLAG 列挙体から取得されます。 STATFLAG 列挙体には2つの値があります  
  
|常時|Value|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1 で保護されたプロセスとして起動されました|  
  
## <a name="remarks"></a>解説  
 ADO Stream オブジェクトに実装されている Stat メソッドのバージョンは、STATSTG 構造体の次のフィールドに入力します。  
  
 *pwcsName*  
 ストリームの名前が含まれていて、StatFlag 値 STATFLAG_NONAME が指定されていない場合は、その名前を格納している文字列。  
  
 *cbSize*  
 ストリームまたはバイト配列のサイズ (バイト単位) を指定します。  
  
 *mtime*  
 このストレージ、ストリーム、またはバイト配列の最終変更時刻を示します。  
  
 *ctime*  
 このストレージ、ストリーム、またはバイト配列の作成時刻を示します。  
  
 *atime*  
 このストレージ、ストリーム、またはバイト配列の最終アクセス時刻を示します。  
  
 StatFlag パラメーターに STATFLAG_NONAME が指定されている場合、ストリームの名前は返されません。  
  
 StatFlag パラメーターに STATFLAG_NONAME が指定されておらず、現在のストリームに使用できる名前がない場合、この値は E_NOTIMPL になります。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
