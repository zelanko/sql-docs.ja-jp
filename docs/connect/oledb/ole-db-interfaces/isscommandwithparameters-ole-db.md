---
title: ISSCommandWithParameters (OLE DB) |Microsoft ドキュメント
description: ISSCommandWithParameters (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5a33a2af2a89a151ae0aeed96a31956037aa036e
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305361"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **ISSCommandWithParameters**インターフェイスのサポートが公開[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]XML、およびユーザー定義型 (UDT)。 これは、主要な OLE DB インターフェイスから継承される省略可能なインターフェイス**ICommandWithParameters**です。 継承される 3 つのメソッドだけでなく**ICommandWithParameters**です。**GetParameterInfo**、 **MapParameterNames**、および**SetParameterInfo**です。**ISSCommandWithParameters**サーバー固有のデータ型を処理するために使用する 2 つの新しいメソッドを提供します。  
  
> [!NOTE]  
>  **ISSCommandWithParameters**サービス コンポーネントを使用すると、サービス コンポーネントは、このインターフェイスを使用しない場合は、インターフェイスを使用することができます。  
  
|方法|説明|  
|------------|-----------------|  
|[Isscommandwithparameters::getparameterproperties &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|1 つを返します**SSPARAMPROPS**プロパティ セット構造体には、コマンドに渡された各 UDT または XML パラメーターの配列が、他の種類のパラメーターに対して none が返されます。|  
|[Isscommandwithparameters::setparameterproperties &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|序数の順に各パラメーターをパラメーターのプロパティを設定またはの配列を指定して一括でパラメーター プロパティを設定**SSPARAMPROPS**構造体。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [XML データ型の使用](../../oledb/features/using-xml-data-types.md)   
 [ユーザー定義型の使用](../../oledb/features/using-user-defined-types.md)  
  
  
