---
title: Charset プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Charset
helpviewer_keywords:
- Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69d65a5330ea83b955629cd9de9684ecc47906ec
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920083"
---
# <a name="charset-property-ado"></a>Charset プロパティ (ADO)
**ストリーム**オブジェクトの内部バッファーに格納するテキスト[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)の内容を変換する文字セットを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **ストリーム**の内容が変換される文字セットを指定する**文字列**値を設定または返します。 既定値は**Unicode**です。 使用できる値は、インターネット文字セット名としてインターフェイスで渡される一般的な文字列です (たとえば、"iso-8859-1"、"Windows-1252" など)。 システムによって認識される文字セット名の一覧については、Windows レジストリの HKEY_CLASSES_ROOT \MIME\Database\Charset のサブキーを参照してください。  
  
## <a name="remarks"></a>Remarks  
 テキスト**ストリーム**オブジェクトでは、テキストデータは**Charset**プロパティによって指定された文字セットに格納されます。 既定値は Unicode です。 **Charset**プロパティは、**ストリーム**に入ってくるデータまたは**ストリーム**から出てくるデータを変換するために使用されます。 たとえば、**ストリーム**に ISO-8859-1 データが含まれていて、そのデータが BSTR にコピーされる場合、**ストリーム**オブジェクトはデータを Unicode に変換します。 この逆も当てはまります。  
  
 開いている**ストリーム**の場合、**文字**セットを設定するには、現在の[位置](../../../ado/reference/ado-api/position-property-ado.md)が**ストリーム**の先頭 (0) である必要があります。  
  
 **Charset**は、テキスト**ストリーム**オブジェクトでのみ使用されます ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 **Type**が**adtypebinary**の場合、このプロパティは無視されます。  
  
 コードサンプルについては、「[手順 4: 詳細を設定する」テキストボックス](../../../ado/guide/data/step-4-populate-the-details-text-box.md)を参照してください。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
