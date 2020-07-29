---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft Docs
description: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 288657a0871046168e7319d5c650a12eab61c6ce
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006752"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SSPARAMPROPS プロパティ セット構造体の配列を返します。各 UDT または XML パラメーターごとに 1 つの SSPARAMPROPS プロパティ セットが返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>引数  
 *pcParams*[out][in]  
 *prgParamProperties* に返された SSPARAMPROPS 構造体の数を保持するメモリへのポインター。  
  
 *prgParamProperties*[out]  
 SSPARAMPROPS 構造体の配列が返されるメモリへのポインター。 プロバイダーは、この構造体用のメモリを割り当て、このメモリのアドレスを返します。コンシューマーは、構造体が不要になった時点で、**IMalloc::Free** を使用してこのメモリを解放します。 コンシューマーは、*prgParamProperties* に対して **IMalloc::Free** を呼び出す前に、各 DBPROP 構造体の *vValue* プロパティに対して **VariantClear** を呼び出す必要があります。これは、変数に参照型 (BSTR など) が含まれている場合にメモリ リークを防ぐためです。 *pcParams* の出力が 0 か、DB_E_ERRORSOCCURRED 以外のエラーが発生した場合は、プロバイダーはメモリの割り当てを行わず、*prgParamProperties* の出力に NULL ポインターを設定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **GetParameterProperties** メソッドは、主要な OLE DB **ICommandProperties::GetProperties** メソッドと同じエラー コードを返します。ただし、DB_S_ERRORSOCCURRED と DB_E_ERRORSOCCURED は返すことができません。  
  
## <a name="remarks"></a>解説  
 **ISSCommandWithParameters::GetParameterProperties** メソッドは、**GetParameterInfo** と一貫性を保つように動作します。 [ISSCommandWithParameters::SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) または **SetParameterInfo** が呼び出されなかったり、cParams に 0 を指定して呼び出した場合は、**GetParameterInfo** はパラメーター情報を取得して、これを返します。 **ISSCommandWithParameters::SetParameterProperties** または **SetParameterInfo** が少なくとも 1 つのパラメーターに対して呼び出されている場合、**ISSCommandWithParameters::GetParameterProperties** メソッドは、**ISSCommandWithParameters::SetParameterProperties** の呼び出しの対象となったパラメーターのプロパティのみを返します。 **ISSCommandWithParameters::SetParameterProperties** が **ISSCommandWithParameters::GetParameterProperties** または **GetParameterInfo** の後に呼び出された場合、後続の **ISSCommandWithParameters::GetParameterProperties** の呼び出しにより、**ISSCommandWithParameters::SetParameterProperties** メソッドの呼び出しの対象となったパラメーターの値がオーバーライドされます。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|メンバー|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|*rgPropertySets* 内の DBPROPSET 構造体の数|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
