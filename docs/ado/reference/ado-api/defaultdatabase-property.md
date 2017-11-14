---
title: "DefaultDatabase プロパティ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a95c2f237a47e5908c5218d45c7d1fa74f87dff9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [プロバイダーと DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [プロバイダーと DefaultDatabase プロパティの使用例 (vc++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   

