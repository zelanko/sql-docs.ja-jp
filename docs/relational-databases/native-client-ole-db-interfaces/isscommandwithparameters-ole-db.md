---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bbdef1bda50ae2d5ace31b56f003e48f8b4bc86b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290199"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **XML および**ユーザー定義型 (UDT) の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サポートを公開します。 これは、コア OLE DB インターフェイス**ICommandWithParameters**から継承する省略可能なインターフェイスです。 から継承された 3 つのメソッドに加えて **、****パラメーター情報**、**割り当てパラメーター名**、および**パラメーターの値を設定**します。**ISSCommandWithParameters は**、サーバー固有のデータ型を処理するために使用される 2 つの新しいメソッドを提供します。  
  
> [!NOTE]  
>  **ISSCommandWithParameters**インターフェイスは、サービス コンポーネントを使用する場合に使用できますが、サービス コンポーネント自体はこのインターフェイスを使用しません。  
  
|Method|説明|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|コマンドに渡された各 UDT パラメーターまたは XML パラメーターごとに、1 つの **SSPARAMPROPS** プロパティ セット構造体を返します。他の型のパラメーターの場合、戻り値はありません。|  
|[ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|序数によってパラメータごとにパラメータプロパティを設定するか **、SSPARAMPROPS**構造体の配列を指定してバルクパラメータプロパティを設定します。|  
  
## <a name="see-also"></a>参照  
 [OLE DB&#41;&#40;インターフェイス](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [XML データ型の使用](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [ユーザー定義型の使用](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
