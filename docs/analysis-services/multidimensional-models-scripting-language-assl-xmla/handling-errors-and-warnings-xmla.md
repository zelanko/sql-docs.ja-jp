---
title: "エラーと警告 (XMLA) 処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1268714f696f852d999a833cf59e69be8c44bb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="handling-errors-and-warnings-xmla"></a>エラーおよび警告の処理 (XMLA)
  XML for Analysis (XMLA) ときに、エラー処理が必要な[Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しは実行されませんが、正常に実行されますが、エラーまたは警告が生成されますまたはが正常に実行結果を返しますエラーが含まれます。  
  
|[エラー]|レポート方法|  
|-----------|---------------|  
|XMLA メソッド呼び出しを実行できない|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]エラーの詳細を含む SOAP エラー メッセージが返されます。<br /><br /> 詳細についてを参照してください、 [SOAP エラーの処理](#handling_soap_faults)です。|  
|メソッド呼び出しは成功したが、エラーまたは警告が発生した|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]含まれています、[エラー](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)または[警告](../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)のエラーまたは警告、要素でそれぞれ、[メッセージ](../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)のプロパティ、[ルート](../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)メソッドの呼び出しの結果を含む要素です。<br /><br /> 詳細についてを参照してください、 [Handling Errors and Warnings](#handling_errors_and_warnings)です。|  
|メソッド呼び出しは成功したが、結果にエラーが含まれる|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インラインを含む**エラー**または**警告**エラーまたは警告のための要素、適切な内で、それぞれ[セル](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)または[行](../../analysis-services/xmla/xml-elements-properties/row-element-xmla.md)メソッドの呼び出しの結果の要素。<br /><br /> 詳細についてを参照してください、[処理インライン エラーおよび警告](#handling_inline_errors_and_warnings)です。|  
  
##  <a name="handling_soap_faults"></a>SOAP エラーの処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、以下の状況が発生した場合に、SOAP エラーを返します。  
  
-   XMLA メソッドを含む SOAP メッセージが、整形式でないか、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって検証できなかった。  
  
-   XMLA メソッドを含む SOAP メッセージに関係する通信エラーまたはその他のエラーが発生した。  
  
-   XMLA メソッドが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで実行できなかった。  
  
 XMLA の SOAP エラー コードは、"XMLForAnalysis" で始まり、その後にピリオドと 16 進数の HRESULT 結果コードが続きます。 たとえば、エラー コード "`0x80000005`" は "`XMLForAnalysis.0x80000005`" という形式になります。 SOAP エラー形式の詳細については、W3C による『Simple Object Access Protocol (SOAP) 1.1』の「Soap Fault」を参照してください。  
  
### <a name="fault-code-information"></a>エラー コード情報  
 次の表は、SOAP 応答の詳細セクションに含まれる XMLA エラー コード情報を示しています。 列は、SOAP エラーの詳細セクションに含まれるエラーの属性です。  
  
|列名|型|Description|Null を許容<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|**ErrorCode**|**UnsignedInt**|メソッドの成功または失敗を示すリターン コード。 16 進数値に変換する必要があります、 **UnsignedInt**値。|不可|  
|**WarningCode**|**UnsignedInt**|警告の状況を示すリターン コード。 16 進数値に変換する必要があります、 **UnsignedInt**値。|はい|  
|**Description**|**文字列**|エラーを生成したコンポーネントによって返されたエラーまたは警告のテキストと説明。|はい|  
|**ソース**|**文字列**|エラーまたは警告を生成したコンポーネントの名前。|はい|  
|**ヘルプ ファイル**|**文字列**|エラーまたは警告について説明しているファイルまたはトピックへのパス、または URL。|はい|  
  
 <sup>1</sup>を示すかどうか、データが必要返す必要があるまたはかどうか、データが省略可能な列が適用されない場合、null 文字列は許可されています。  
  
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
  
##  <a name="handling_errors_and_warnings"></a>エラーおよび警告の処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]返します、**メッセージ**プロパティに、**ルート**コマンドの実行後に、次の状況が発生する場合、コマンドの要素。  
  
-   メソッド自体は失敗しなかったが、メソッドが成功した後に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでエラーが発生した。  
  
-   コマンドが成功したときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって警告が返される。  
  
 **メッセージ**プロパティに含まれる他のすべてのプロパティに依存して、**ルート**要素、1 つ以上含めることができます**メッセージ**要素。 各**メッセージ**要素は、1 つを含めることができます**エラー**または**警告**で発生したエラーまたは警告をそれぞれ説明する要素の指定されたコマンド。  
  
 含まれるされたエラーと警告の詳細については、**メッセージ**プロパティを参照してください[メッセージ要素 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md).  
  
### <a name="handling-errors-during-serialization"></a>シリアル化実行時のエラーの処理  
 後にエラーが発生した場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスが正常に実行のコマンドの出力のシリアル化を開始した[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を返します、[例外](../../analysis-services/xmla/xml-elements-properties/exception-element-xmla.md)エラーの時点で別の名前空間内の要素。 その後 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、クライアントに送信する XML ドキュメントが有効なドキュメントになるように、開いている要素をすべて閉じます。 インスタンスが返されます、**メッセージ**エラーの説明を格納する要素。  
  
##  <a name="handling_inline_errors_and_warnings"></a>インライン エラーおよび警告の処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インラインを返します**エラー**または**警告**XMLA メソッド自体は失敗しなかったのメソッドによって返される結果のデータ要素に固有のエラーが発生した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]XMLA メソッド呼び出しが成功した後のインスタンス。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インラインの提供**エラー**と**警告**セルやその他のデータに特定の問題である場合、要素内に含まれる、**ルート**要素を使用して、 [MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)セキュリティ エラーやセルのフォーマット エラーなどのデータ型が発生します。 このような場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を返します、**エラー**または**警告**内の要素、**セル**または**行**エラーを含む要素または警告、それぞれします。  
  
 次の例では、結果セットから返される行セットでエラーが発生した、 **Execute**メソッドを使用して、[ステートメント](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)コマンド。  
  
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
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

