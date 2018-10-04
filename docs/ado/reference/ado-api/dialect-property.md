---
title: Dialect プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef18eb3d6251bc07ae25ef8cbc3445a87b8390b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810520"
---
# <a name="dialect-property"></a>Dialect プロパティ
言語を示します、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)または[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)プロパティ。 言語仕様では、構文と、プロバイダーを使用して文字列またはストリームを解析するための一般的な規則を定義します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **言語**プロパティには、コマンド文字列またはストリームの言語を表す有効な GUID が含まれています。 このプロパティの既定値は {C8B521FB-5CF3-11CE-ADE5-00AA0044773D} を示す、プロバイダーがコマンド文字列またはストリームを解釈する方法を選択する必要があります。  
  
## <a name="remarks"></a>コメント  
 ADO は、ユーザーがこのプロパティの値を読み取るときに、プロバイダーを照会できません。格納されている値の文字列表現を返します、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
 ユーザーが設定した場合、**言語**プロパティ、ADO は、GUID を検証し、指定された値が有効な GUID ではない場合は、エラーを発生させます。 サポートされている GUID 値を決定する、プロバイダーのドキュメントを参照して、**言語**プロパティ。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Execute メソッド (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md)
