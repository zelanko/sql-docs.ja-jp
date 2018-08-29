---
title: ISSCommandWithParameters (OLE DB) |Microsoft Docs
description: ISSCommandWithParameters (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 6dcd2f0466a4da6226a9fb363d5d7028ccaa6bee
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031240"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **ISSCommandWithParameters** インターフェイスでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の XML と UDT (ユーザー定義型) のサポートが公開されます。 これは、主要な OLE DB インターフェイス **ICommandWithParameters** から継承される省略可能なインターフェイスです。 **ISSCommandWithParameters** には、**ICommandWithParameters** から継承される **GetParameterInfo**、**MapParameterNames**、および **SetParameterInfo** という 3 つのメソッドに加えて、サーバー固有のデータ型の処理に使用する 2 つの新しいメソッドが用意されています。  
  
> [!NOTE]  
>  **ISSCommandWithParameters** インターフェイスは、サービス コンポーネントを使用している場合に使用できますが、サービス コンポーネントがこのインターフェイスを使用することはありません。  
  
|方法|[説明]|  
|------------|-----------------|  
|[Isscommandwithparameters::getparameterproperties &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|コマンドに渡された各 UDT パラメーターまたは XML パラメーターごとに、1 つの **SSPARAMPROPS** プロパティ セット構造体を返します。他の型のパラメーターの場合、戻り値はありません。|  
|[Isscommandwithparameters::setparameterproperties &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|序数順に各パラメーターのパラメーター プロパティを設定するか、**SSPARAMPROPS** 構造体の配列を指定して、一括でパラメーター プロパティを設定します。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [XML データ型の使用](../../oledb/features/using-xml-data-types.md)   
 [ユーザー定義型の使用](../../oledb/features/using-user-defined-types.md)  
  
  
