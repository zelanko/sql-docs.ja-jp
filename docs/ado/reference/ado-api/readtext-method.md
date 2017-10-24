---
title: "ReadText メソッド |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_ReadText
- _Stream::ReadText
helpviewer_keywords:
- ReadText method [ADO]
ms.assetid: be5a409e-cf87-4859-9ea5-713401755a77
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b134e064cc3d1dfa06c5d948d74e49f643756bd1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="readtext-method"></a>ReadText メソッド
指定されたテキストの文字数を読み取ります[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *NumChars*  
 省略可。 A**長い**ファイルから読み取る文字の数を指定する値または[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)値。 既定値は**adReadAll**です。  
  
## <a name="return-value"></a>戻り値  
 **ReadText**メソッドは、指定された文字数、行全体、またはからストリーム全体を読み取ります、**ストリーム**オブジェクトし、結果の文字列を返します。  
  
## <a name="remarks"></a>解説  
 場合*NumChar*ストリームに残りますが、文字数よりも多い、残りの文字のみが返されます。 指定された長さに一致する文字列の読み取りが埋め込まれていません*NumChar*です。 読み取る文字がない場合は、バリアント型を持つ値は null が返されます。 **ReadText**旧バージョンと読み取りに使用することはできません。  
  
> [!NOTE]
>  **ReadText**メソッドがテキスト ストリームで使用される ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 バイナリ ストリームの (**型**は**adTypeBinary**)、使用して[読み取り](../../../ado/reference/ado-api/read-method.md)です。  
  
 クエリから返される XML データを大量になる、 **ReadText** ActiveX データ オブジェクト (ADO) ストリーム オブジェクトのメソッドは、これは、COM + コンポーネントから呼び出された場合です実行にかかる時間を大幅に向上にかかる場合があります、。ASP ページで、ユーザーのセッションはタイムアウトします。ADO から utf-8 エンコードが Unicode; にストリーム オブジェクトのデータを変換します一度に大量のデータの変換に関連する頻繁なメモリの再割り当ては非常に時間がかかる場合です。 解決するにを繰り返し呼び出す、 **ReadText**を ADO コマンド オブジェクト、およびより小さい文字数を指定します。 テストによる 128 K (131,072) と同じ値が最適であります。 この値がよりも減少した応答時間が低下します。 詳細については、サポート技術情報の記事 280067 を参照してください。"[prb]: 速度が低下する可能性があります ADO ストリーム オブジェクトの ReadText メソッドを使用して SQL Server 2000 から非常に大きな XML ドキュメントを取得する"、http://support.microsoft.com で Microsoft サポート技術情報でします。  
  
## <a name="applies-to"></a>適用対象  
 [ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Read メソッド](../../../ado/reference/ado-api/read-method.md)

