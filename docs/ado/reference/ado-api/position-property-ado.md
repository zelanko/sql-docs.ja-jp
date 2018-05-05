---
title: Position プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Position
helpviewer_keywords:
- Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c931d220a9418a790ff79d6b61c89004800a0061
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="position-property-ado"></a>位置プロパティ (ADO)
内の現在位置を示す、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**バイト、ストリームの先頭から現在の位置の数でオフセットを指定する値。 既定では 0 で、ストリーム内の最初のバイトを表します。  
  
## <a name="remarks"></a>解説  
 現在の位置は、ストリームの末尾の後に、ポイントに移動できます。 ストリームの末尾を越える現在位置を指定する場合、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)の**ストリーム**オブジェクトがそれに応じて増加します。 この方法で追加された新しいバイトは、null になります。  
  
> [!NOTE]
>  **位置**常にバイトを測定します。 テキスト ストリームはマルチバイト文字セットを使用して、位置の文字数を決定する、文字のサイズを掛けます。 たとえば、2 バイト文字セットでは、最初の文字は、位置 0、2、3 番目の文字位置にある 2 番目の文字の位置 4、およびながします。  
  
> [!NOTE]
>  内の現在位置を変更するのには、負の値を使用できません、**ストリーム**です。 正の数値だけを使用できます**位置**です。  
  
> [!NOTE]
>  読み取り専用**ストリーム**オブジェクトの場合は、ADO はエラーを返しません。**位置**より大きい値に設定されて、**サイズ**の、**ストリーム**です。 サイズは変わりません、**ストリーム**、alter、または、**ストリーム**任意の方法で内容。 ただし、これを行う避ける必要がありますので、無意味な**位置**値。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Charset プロパティ (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
