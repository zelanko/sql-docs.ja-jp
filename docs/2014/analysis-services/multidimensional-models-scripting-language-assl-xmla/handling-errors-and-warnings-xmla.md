---
title: エラーと警告の処理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07b88d800237e5b4b06af0c1ff11cbd0af846600
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545014"
---
# <a name="handling-errors-and-warnings-xmla"></a>エラーおよび警告の処理 (XMLA)
  エラー処理は、XML for Analysis (XMLA) の[Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)または[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドの呼び出しが実行されず、正常に実行されるがエラーまたは警告が生成される場合、または正常に実行されてもエラーを含む結果が返される場合に必要です。  
  
|エラー|レポート|  
|-----------|---------------|  
|XMLA メソッド呼び出しを実行できない|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エラーの詳細を含む SOAP エラーメッセージを返します。<br /><br /> 詳細については、「 [SOAP エラーの処理](#handling_soap_faults)」を参照してください。|  
|メソッド呼び出しは成功したが、エラーまたは警告が発生した|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、各エラーまたは警告について、メソッド呼び出しの結果を含む[ルート](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)要素の[Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)プロパティに、[エラー](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)または[警告](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla)の要素がそれぞれ含まれています。<br /><br /> 詳細については、「[エラーと警告の処理](#handling_errors_and_warnings)」を参照してください。|  
|メソッド呼び出しは成功したが、結果にエラーが含まれる|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]には、 `error` `warning` メソッド呼び出しの結果の適切な[セル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)または[行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla)要素内に、エラーまたは警告のインラインまたは要素がそれぞれ含まれています。<br /><br /> 詳細については、「[インラインエラーと警告の処理](#handling_inline_errors_and_warnings)」を参照してください。|  
  
##  <a name="handling-soap-faults"></a><a name="handling_soap_faults"></a>SOAP エラーの処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、以下の状況が発生した場合に、SOAP エラーを返します。  
  
-   XMLA メソッドを含む SOAP メッセージが、整形式でないか、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって検証できなかった。  
  
-   XMLA メソッドを含む SOAP メッセージに関係する通信エラーまたはその他のエラーが発生した。  
  
-   XMLA メソッドが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで実行できなかった。  
  
 XMLA の SOAP エラー コードは、"XMLForAnalysis" で始まり、その後にピリオドと 16 進数の HRESULT 結果コードが続きます。 たとえば、エラー コード "`0x80000005`" は "`XMLForAnalysis.0x80000005`" という形式になります。 SOAP エラー形式の詳細については、W3C による『Simple Object Access Protocol (SOAP) 1.1』の「Soap Fault」を参照してください。  
  
### <a name="fault-code-information"></a>エラー コード情報  
 次の表は、SOAP 応答の詳細セクションに含まれる XMLA エラー コード情報を示しています。 列は、SOAP エラーの詳細セクションに含まれるエラーの属性です。  
  
|列名|種類|説明|Null 値が許可されます<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|メソッドの成功または失敗を示すリターン コード。 16 進数値は、`UnsignedInt` の値に変換する必要があります。|いいえ|  
|`WarningCode`|`UnsignedInt`|警告の状況を示すリターン コード。 16 進数値は、`UnsignedInt` の値に変換する必要があります。|はい|  
|`Description`|`String`|エラーを生成したコンポーネントによって返されたエラーまたは警告のテキストと説明。|はい|  
|`Source`|`String`|エラーまたは警告を生成したコンポーネントの名前。|はい|  
|`HelpFile`|`String`|エラーまたは警告について説明しているファイルまたはトピックへのパス、または URL。|はい|  
  
 <sup>1</sup>は、データが必須であり、返される必要があるかどうか、またはデータが省略可能であり、列が適用されない場合は null 文字列が許可されるかどうかを示します。  
  
 次は、メソッド呼び出しが失敗した場合に発生した SOAP エラーの例です。  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling-errors-and-warnings"></a><a name="handling_errors_and_warnings"></a>エラーと警告の処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、コマンドの実行後に以下の状況が発生した場合、`Messages` 要素内に `root` プロパティを返します。  
  
-   メソッド自体は失敗しなかったが、メソッドが成功した後に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでエラーが発生した。  
  
-   コマンドが成功したときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって警告が返される。  
  
 `Messages` プロパティは、`root` 要素に含まれる他のすべてのプロパティの後に続きます。このプロパティには、1 つ以上の `Message` 要素が含まれます。 さらに、各 `Message` 要素には、指定されたコマンドで発生したエラーまたは警告についてそれぞれ説明する 1 つの `error` または `warning` 要素のいずれかが含まれます。  
  
 プロパティに含まれるエラーと警告の詳細につい `Messages` ては、「 [Messages 要素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)」を参照してください。  
  
### <a name="handling-errors-during-serialization"></a>シリアル化実行時のエラーの処理  
 インスタンスが正常に実行されたコマンドの出力のシリアル化を既に開始した後にエラーが発生した場合 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エラーの時点で別の名前空間の[Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla)要素を返します。 その後 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、クライアントに送信する XML ドキュメントが有効なドキュメントになるように、開いている要素をすべて閉じます。 インスタンスは、エラーの説明を含む `Messages` 要素も返します。  
  
##  <a name="handling-inline-errors-and-warnings"></a><a name="handling_inline_errors_and_warnings"></a>インラインエラーと警告の処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、XMLA メソッド自体は失敗しなかったものの、XMLA メソッド呼び出しが成功した後に、メソッドによって返された結果内のデータ要素に固有のエラーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで発生した場合、インライン `error` または `warning` を返します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]セルに `error` `warning` 固有の問題、または mddataset データ型を使用して要素内に含まれるその他のデータに固有の問題がある場合は、インライン要素と要素を提供し `root` ます。たとえば、セキュリティエラーやセルの書式設定エラーなどです。 [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) そのような場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、エラーまたは警告を含む `error` または `warning` 要素に、`Cell` または `row` 要素をそれぞれ返します。  
  
 次の例では、 `Execute` [ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを使用して、メソッドから返された行セットのエラーを含む結果セットを示します。  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
