---
title: Isscommandwithparameters::setparameterproperties (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f17947c2b5eb0a8438c074ffca34dca728ae859a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076869"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
  序数順に各パラメーターのパラメーター プロパティを設定するか、SSPARAMPROPS 構造体の配列を指定して、一括でパラメーター プロパティを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>引数  
 *cParams*[in]  
 数、SSPARAMPROPS 構造体に、 *rgParamProperties*配列。 この数が 0 の場合`ISSCommandWithParameters::SetParameterProperties`コマンドのパラメーターの指定されたすべてのプロパティが削除されます。  
  
 *rgParamProperties*[in]  
 設定する SSPARAMPROPS 構造体の配列。  
  
## <a name="return-code-values"></a>リターン コードの値  
 `ISSCommandWithParameters::SetParameterProperties`メソッドは、主要な OLE DB と同じエラー コードを返します**icommandproperties::setproperties**メソッドです。  
  
## <a name="remarks"></a>コメント  
 このメソッドを使用してパラメーター プロパティを設定または許可されて、各パラメーターごとに、序数を 1 つの`ISSCommandWithParameters::SetParameterProperties`プロパティ配列から SSPARAMPROPS が構築された 1 回呼び出します。  
  
 **SetParameterInfo**メソッドを呼び出す前に呼び出す必要があります、`ISSCommandWithParameters::SetParameterProperties`メソッドです。 `SetParameterProperties(0, NULL)` を呼び出すと、指定したパラメーター プロパティがすべて消去されます。また、`SetParameterInfo(0,NULL,NULL)` を呼び出すと、パラメーターに関連付けられているすべてのプロパティを含めて、パラメーターに関するすべての情報が消去されます。  
  
 呼び出す`ISSCommandWithParameters::SetParameterProperties`はない型のパラメーターのプロパティを指定する dbtype_xml 型または dbtype_udt 型を返します DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED とマーク、 *dwStatus* SSPARAMPROPS に含まれているすべての Dbprop のフィールドdbpropstatus_notset パラメーター。 DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が指しているパラメーターを検出するには、SSPARAMPROPS に含まれている各 DBPROPSET の DBPROP 配列をすべて調べる必要があります。  
  
 場合`ISSCommandWithParameters::SetParameterProperties`がパラメーター ヒントがまだ設定されていないパラメーターのプロパティを指定するために呼び出される**SetParameterInfo**プロバイダーは、次のエラー メッセージと共に E_UNEXPECTED を返します。  
  
 パラメーターを指定して SetParameterProperties メソッドを呼び出す場合は、最初に SetParameterInfo メソッドを呼び出す必要があります。 パラメーターのプロパティを設定する前に、パラメーター情報を設定する必要があります。  
  
 場合に呼び出し`ISSCommandWithParameters::SetParameterProperties`パラメーター ヒントが設定されている、いくつかのパラメーター、パラメーター情報が設定されていない、SSPARAMPROPS プロパティ セットの DBPROPSET 内の dwStatus プロパティに DBSTATUS_NOTSET が返さいくつかのパラメーターが含まれています。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 以降で、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]isscommandwithparameters::setparameterproperties を期待する結果のより正確な記述を取得できるようにします。 以前のバージョンの isscommandwithparameters::setparameterproperties によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../native-client/features/metadata-discovery.md)です。  
  
|Member|説明|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|DBPROPSET の数が構造体に*rgPropertySets*です。|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  