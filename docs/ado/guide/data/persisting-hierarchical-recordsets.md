---
title: 階層レコード セットの保持 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f25b61ca54b3a4ac15584ecf31874f90787c735d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700471"
---
# <a name="persisting-hierarchical-recordsets"></a>階層レコードセットの保持
階層構造を保存する**レコード セット**を呼び出すことによって、adtg 形式または XML 形式でファイルに、[保存](../../../ado/reference/ado-api/save-method.md)メソッド。 階層を保存するときに、2 つの制限を適用するただし、**レコード セット**XML 形式で s。場合は、XML で保存することはできません、階層**レコード セット**保留中の更新プログラムが含まれています。 パラメーター化されたを保存することはできませんと階層**レコード セット**します。  
  
 データ シェイプ プロバイダーの詳細については、次を参照してください。 [Microsoft Data Shaping Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) と[for OLE DB Data Shaping Service の概要](https://msdn.microsoft.com/9f51e471-8e85-448e-9fb8-b64bbf767bf3)します。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [Shape の正式文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
