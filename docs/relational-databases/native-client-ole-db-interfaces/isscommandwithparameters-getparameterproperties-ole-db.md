---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 26c95c64f0f2922ef11946841b160879f001e358
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290082"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SSPARAMPROPS プロパティ セット構造体の配列を返します。各 UDT または XML パラメーターごとに 1 つの SSPARAMPROPS プロパティ セットが返されます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>引数  
 *pcParams*[out][in]  
 *prgParamProperties* に返された SSPARAMPROPS 構造体の数を保持するメモリへのポインター。  
  
 *prgParamProperties*[out]  
 SSPARAMPROPS 構造体の配列が返されるメモリへのポインター。 プロバイダーは構造体のメモリを割り当て、このメモリにアドレスを返します。このメモリは、構造体が不要になった場合に**IMalloc::Free で**解放されます。 **IMalloc::Free** for *prgParamProperties*を呼び出す前に、バリアントに参照型 (BSTR など) が含まれる場合にメモリ リークが発生しないように、各 DBPROP 構造体の*vValue*プロパティの**VariantClear**も呼び出す必要があります。*pcParams*が出力時にゼロであるか、DB_E_ERRORSOCCURRED以外のエラーが発生した場合、プロバイダはメモリを割り当てず *、prgParamProperties*が出力時に null ポインタであることを確認します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 メソッド**は**、DB_S_ERRORSOCCURREDとDB_E_ERRORSOCCUREDを発生させることができないことを除いて、コア OLE DB **ICommandProperties::GetProperties**メソッドと同じエラー コードを返します。  
  
## <a name="remarks"></a>解説  
 **パラメーター::GetParameter プロパティ**は **、GetParameterInfo**に関して一貫して動作します。 呼び出されていないか[、0](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)に等しい**SetParameterInfo**cParams で呼び出されている場合は、**パラメーター**情報を派生し、これを返します。 少なくとも 1 つのパラメーターに対して呼び**SetParameterInfo**出されたパラメーターが**ISSCommandWithParameters::SetParameter プロパティ**である場合は、プロパティが返されます。 **ISSCommandWithParameters::SetParameterProperties** **ISSCommandWithParameters::GetParameterProperties** **ISS コマンド付きパラメーター::SetParameter プロパティ**が呼び出された場合**は、次に呼び**出されます。 **GetParameterInfo** **ISSCommandWithParameters::GetParameterProperties** **ISSCommandWithParameters::SetParameterProperties**  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  

```cpp
struct SSPARAMPROPS {
    DBORDINAL iOrdinal;
    ULONG cPropertySets;
    DBPROPSET *rgPropertySets;
};
```

|メンバー|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|*rgPropertySets* 内の DBPROPSET 構造体の数|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
|||

## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
