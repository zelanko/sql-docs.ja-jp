---
title: Dialect プロパティ |Microsoft ドキュメント
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
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74299cc953c3ac94653860d18d0ee7774ecf49ad
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dialect-property"></a>Dialect プロパティ
言語を示す、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)または[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)プロパティです。 言語仕様では、構文と、プロバイダーを使用して文字列またはストリームを解析するための一般的な規則を定義します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **Dialect**プロパティには、コマンド文字列またはストリームの言語を表す有効な GUID が含まれています。 このプロパティの既定値は {C8B521FB-5CF3-11CE-ADE5-00AA0044773D} を示す、プロバイダーがコマンド文字列またはストリームを解釈する方法を選択する必要があります。  
  
## <a name="remarks"></a>解説  
 ADO は、ユーザーがこのプロパティの値を読み取るときに、プロバイダーを照会できません。格納されている値の文字列表現を返します、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
 ユーザーが設定した場合、 **Dialect**プロパティ、ADO は GUID を検証し、指定された値が有効な GUID ではないエラーが発生します。 サポートされている GUID 値を決定する、プロバイダーのマニュアルを参照して、 **Dialect**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Execute メソッド (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md)
