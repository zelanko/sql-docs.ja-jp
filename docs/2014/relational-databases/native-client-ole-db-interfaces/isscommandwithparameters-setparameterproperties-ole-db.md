---
title: 'ISSCommandWithParameters:: SetParameterProperties (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 778021ce007f0c1eac68197e0c07e2cb7b0bb001
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62638770"
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
 *Cparams*[in]  
 
  *rgParamProperties* 配列内の SSPARAMPROPS 構造体の数。 この数値が0の場合`ISSCommandWithParameters::SetParameterProperties`は、コマンドのパラメーターに指定されている可能性のあるすべてのプロパティが削除されます。  
  
 *rgParamProperties*[in]  
 設定する SSPARAMPROPS 構造体の配列。  
  
## <a name="return-code-values"></a>リターン コードの値  
 この`ISSCommandWithParameters::SetParameterProperties`メソッドは、コア OLE DB **ICommandProperties:: SetProperties**メソッドと同じエラーコードを返します。  
  
## <a name="remarks"></a>解説  
 このメソッドを使用してパラメーターのプロパティを設定できるのは、序数によってパラメーター `ISSCommandWithParameters::SetParameterProperties`ごとに指定するか、または SSPARC amprops がプロパティ配列から構築された1回の呼び出しで許可されます。  
  
 メソッドを`ISSCommandWithParameters::SetParameterProperties`呼び出す前に**setparameterinfo**メソッドを呼び出す必要があります。 
  `SetParameterProperties(0, NULL)` を呼び出すと、指定したパラメーター プロパティがすべて消去されます。また、`SetParameterInfo(0,NULL,NULL)` を呼び出すと、パラメーターに関連付けられているすべてのプロパティを含めて、パラメーターに関するすべての情報が消去されます。  
  
 を`ISSCommandWithParameters::SetParameterProperties`呼び出して、DBTYPE_XML 型または DBTYPE_UDT 型ではないパラメーターのプロパティを指定すると、DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が返され、そのパラメーターの SSPARAMPROPS に含まれるすべての dbprops の*dwstatus*フィールドが DBPROPSTATUS_NOTSET でマークされます。 DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が指しているパラメーターを検出するには、SSPARAMPROPS に含まれている各 DBPROPSET の DBPROP 配列をすべて調べる必要があります。  
  
 パラメーター `ISSCommandWithParameters::SetParameterProperties`情報が**setparameterinfo**でまだ設定されていないパラメーターのプロパティを指定するためにが呼び出された場合、プロバイダーは次のエラーメッセージと共に E_UNEXPECTED を返します。  
  
 パラメーターを指定して SetParameterProperties メソッドを呼び出す場合は、最初に SetParameterInfo メソッドを呼び出す必要があります。 パラメーターのプロパティを設定する前に、パラメーター情報を設定する必要があります。  
  
 パラメーターヒントが設定`ISSCommandWithParameters::SetParameterProperties`されているいくつかのパラメーターと、パラメーター情報が設定されていないパラメーターがの呼び出しに含まれている場合、SDBPROPSET amprops プロパティセットの dwstatus プロパティは DBSTATUS_NOTSET を返します。  
  
 SSPARAMPROPS 構造体は、次のように定義されています。  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 で始まるデータベースエンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ISSCommandWithParameters:: SetParameterProperties を使用すると、予期される結果についてより正確な説明を取得できます。 これらのより正確な結果は、以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で ISSCommandWithParameters:: SetParameterProperties によって返される値とは異なる場合があります。 詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。  
  
|メンバー|[説明]|  
|------------|-----------------|  
|*iOrdinal*|渡されるパラメーターの序数|  
|*cPropertySets*|
  *rgPropertySets* 内の DBPROPSET 構造体の数|  
|*rgPropertySets*|DBPROPSET 構造体の配列を返すメモリへのポインター|  
  
## <a name="see-also"></a>参照  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
