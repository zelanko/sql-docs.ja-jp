---
title: DefaultDatabase プロパティ |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a62362ea626155c002a291185c935163b1126e28
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="defaultdatabase-property"></a>DefaultDatabase プロパティ
既定のデータベースを示す、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**プロバイダーから使用可能なデータベースの名前に評価される値。  
  
## <a name="remarks"></a>解説  
 使用して、 **DefaultDatabase**プロパティを設定または特定の既定のデータベースの名前を返す**接続**オブジェクト。  
  
 既定のデータベースがある場合、SQL 文字列は、そのデータベース内のオブジェクトにアクセスする構文が不適切なを使用する場合があります。 指定した以外のデータベースにオブジェクトにアクセスする、 **DefaultDatabase**プロパティ、目的のデータベース名でオブジェクト名を修飾する必要があります。 接続時に、プロバイダーが既定のデータベース情報を書き込む、 **DefaultDatabase**プロパティです。 一部のプロバイダーは接続ごとに 1 つだけデータベースを許可する、その場合で変更することはできません、 **DefaultDatabase**プロパティです。  
  
 一部のデータ ソースとプロバイダーはこの機能をサポートしていませんし、エラーまたは空の文字列を返す可能性があります。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**このプロパティはクライアント側で使用できません**接続**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [プロバイダーと DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider および DefaultDatabase プロパティの例 (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
