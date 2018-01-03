---
title: "Charset プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: _Stream::Charset
helpviewer_keywords: Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efa963c26617a382270ccf2ed25f1aeb5c9785d4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="charset-property-ado"></a>Charset プロパティ (ADO)
文字セットを示します、テキストの内容[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)の内部バッファーに格納するために変換するか、**ストリーム**オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**文字を指定する値の設定先の内容、**ストリーム**変換されます。 既定値は**Unicode**です。 有効な値は、インターネットの文字セットの名前 (たとえば、および「iso 8859-1」、"windows-1252") として、インターフェイス経由で渡される一般的な文字列です。 システムによって把握されている文字セット名の一覧は、Windows レジストリに HKEY_CLASSES_ROOT\MIME\Database\Charset のサブキーを参照してください。  
  
## <a name="remarks"></a>解説  
 テキストの**ストリーム**オブジェクト、文字セットで指定されたテキスト データが格納されている、 **Charset**プロパティです。 既定では Unicode です。 **Charset**プロパティに入るデータを変換するため、**ストリーム**または今後のうち、**ストリーム**です。 たとえば場合、**ストリーム**ISO 8859-1 のデータ、BSTR へのデータのコピーが含まれています、**ストリーム**オブジェクトは、データを Unicode に変換されます。 この逆も当てはまります。  
  
 開くのため**ストリーム**、現在[位置](../../../ado/reference/ado-api/position-property-ado.md)の先頭にある必要があります、**ストリーム**(0) に設定できる**Charset**です。  
  
 **Charset**はテキストでのみ使用**ストリーム**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 場合、このプロパティは無視されます**型**は**adTypeBinary**です。  
  
 コード サンプルでは、次を参照してください。[手順 4: 詳細テキスト ボックスに入力](../../../ado/guide/data/step-4-populate-the-details-text-box.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
