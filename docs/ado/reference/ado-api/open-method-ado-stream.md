---
title: "Open メソッド (ADO ストリーム) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_Open
- _Stream::Open
helpviewer_keywords: Open method [ADO]
ms.assetid: d26f48fb-904e-4932-a245-3b4332ca1600
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2da6a07f58ab3cceb9ca9d661703603146c3e5f6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="open-method-ado-stream"></a>Open メソッド (ADO Stream)
開く、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)バイナリまたはテキスト データのストリームを操作するオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 省略可。 A**バリアント**のデータ ソースを指定する値、**ストリーム**です。 *ソース*電子メールまたはファイル システムなどのよく知られているツリー構造内の既存のノードを指す絶対 URL 文字列を含めることがあります。 URL のキーワードを使用して、URL を指定する必要があります ("URL =*スキーム*://*サーバー*/*フォルダー*") です。 または、*ソース*既に開かれているへの参照を含めることは[レコード](../../../ado/reference/ado-api/record-object-ado.md)に関連付けられている既定のストリームを開き、オブジェクト、**レコード**です。 場合*ソース*が指定されていない、**ストリーム**インスタンス化し、開くと、既定ではない基になるソースに関連付けられているがします。 URL スキームおよび関連するプロバイダーの詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
 *モード*  
 省略可。 A [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) 、結果のアクセス モードを指定する値**ストリーム**(たとえば、読み取り/書き込みまたは読み取り専用)。 既定値は**adModeUnknown**です。 参照してください、[モード](../../../ado/reference/ado-api/mode-property-ado.md)アクセス モードの詳細についてはプロパティです。 場合*モード*が指定されていない、ソース オブジェクトによって継承されます。 たとえば場合、ソース**レコード**が読み取り専用モードで開かれる、**ストリーム**既定では読み取り専用モードでも開かれます。  
  
 *OpenOptions*  
 省略可。 A [StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)値。 既定値は**adOpenStreamUnspecified**です。  
  
 *UserName*  
 省略可。 A**文字列**、必要な場合にアクセスするユーザー id を表す値、**ストリーム**オブジェクト。  
  
 *Password*  
 省略可。 A**文字列**、必要な場合にアクセスするパスワードを含む値、**ストリーム**オブジェクト。  
  
## <a name="remarks"></a>解説  
 ときに、**レコード**オブジェクト ソースのパラメーターとして渡される、 *UserID*と*パスワード*ためパラメーターを使用しないへのアクセス、**レコード**オブジェクトが既に使用可能です。 同様に、[モード](../../../ado/reference/ado-api/mode-property-ado.md)の**レコード**にオブジェクトを転送、**ストリーム**オブジェクト。 ときに*ソース*が指定されていない、**ストリーム**開かれたデータが含まれており、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)ゼロ (0) です。 これに書き込まれるデータの損失を回避する**ストリーム**ときに、**ストリーム**を閉じると、保存、**ストリーム**で、 [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)または[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)メソッド、または別のメモリ位置に保存します。  
  
 *OpenOptions*値**adOpenStreamFromRecord**の内容を識別、*ソース*パラメーターを既に開いている**レコード**オブジェクト。 既定の動作が扱わ*ソース*ファイルなどのツリー構造でノードを直接参照する URL として。 そのノードに関連付けられている既定のストリームが開かれます。  
  
 中に、**ストリーム**が開いていない場合はのすべての読み取り専用のプロパティの読み取り可能な**ストリーム**です。 場合、**ストリーム**を開いたすべての後続の操作では、非同期的に (以外のチェック、[状態](../../../ado/reference/ado-api/state-property-ado.md)およびその他の読み取り専用のプロパティ) までブロックされて、**開く**操作が完了したとします。  
  
 指定しないことにより、前に説明したオプションに加え*ソース*のインスタンスを作成することができます、**ストリーム**せず、基になるソースに関連付けることがメモリ内のオブジェクト。 バイナリまたはテキスト データを記述してデータをストリームに動的に追加することができます、**ストリーム**で[書き込み](../../../ado/reference/ado-api/write-method.md)または[WriteText](../../../ado/reference/ado-api/writetext-method.md)、または使用してファイルからデータを読み込むことにより[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO レコード)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)   
 [SaveToFile メソッド](../../../ado/reference/ado-api/savetofile-method.md)
