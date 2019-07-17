---
title: Isscommandwithparameters::setparameterproperties (OLE DB) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0e4ec4a160920d8490cb7578de76656a1253adac
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050965"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  序数順に各パラメーターのパラメーター プロパティを設定するか、SSPARAMPROPS 構造体の配列を指定して、一括でパラメーター プロパティを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>引数  
 *cParams*[in]  
 *rgParamProperties* 配列内の SSPARAMPROPS 構造体の数。 この数が 0 の場合、**ISSCommandWithParameters::SetParameterProperties** では、コマンドのパラメーターに指定されているすべてのプロパティを削除します。  
  
 *rgParamProperties*[in]  
 設定する SSPARAMPROPS 構造体の配列。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **ISSCommandWithParameters::SetParameterProperties** メソッドでは、主要な OLE DB **ICommandProperties::SetProperties** メソッドと同じエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドを使用したパラメーター プロパティの設定は、各パラメーターに対して序数順に行うか、プロパティ配列から SSPARAMPROPS が構築されるたびに **ISSCommandWithParameters::SetParameterProperties** を 1 回呼び出すことによって行うことができます。  
  
 **ISSCommandWithParameters::SetParameterProperties** メソッドを呼び出す前に、**SetParameterInfo** メソッドを呼び出す必要があります。 `SetParameterProperties(0, NULL)` を呼び出すと、指定したパラメーター プロパティがすべて消去されます。また、`SetParameterInfo(0,NULL,NULL)` を呼び出すと、パラメーターに関連付けられているすべてのプロパティを含めて、パラメーターに関するすべての情報が消去されます。  
  
 呼び出す**isscommandwithparameters::setparameterproperties**のない型のパラメーター プロパティを指定する dbtype_xml 型または DBTYPE_UDT 返します DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED とマーク、 *dwStatus* dbpropstatus_notset そのパラメーターの SSPARAMPROPS に含まれているすべてのときのフィールド。 DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が指しているパラメーターを検出するには、SSPARAMPROPS に含まれている各 DBPROPSET の DBPROP 配列をすべて調べる必要があります。  
  
 **ISSCommandWithParameters::SetParameterProperties** を呼び出すときに、**SetParameterInfo** によって情報が設定されていないパラメーターのプロパティを指定すると、プロバイダーは次のエラー メッセージと共に E_UNEXPECTED を返します。  
  
 パラメーターを指定して SetParameterProperties メソッドを呼び出す場合は、最初に SetParameterInfo メソッドを呼び出す必要があります。 パラメーターのプロパティを設定する前に、パラメーター情報を設定する必要があります。  
  
 **ISSCommandWithParameters::SetParameterProperties** を呼び出すときに、情報が設定されているパラメーターと設定されていないパラメーターが含まれている場合、SSPARAMPROPS プロパティ セットの DBPROPSET 内の dwStatus プロパティに DBSTATUS_NOTSET が設定されて返されます。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 以降では、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]isscommandwithparameters::setparameterproperties 期待どおりの結果のより正確な記述を取得できるようにします。 これらのより正確な結果の以前のバージョンの isscommandwithparameters::setparameterproperties によって返される値が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)します。  
  
|Member|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|*rgPropertySets* 内の DBPROPSET 構造体の数|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
