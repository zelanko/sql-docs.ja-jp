---
title: エラーおよび警告 (XMLA) の処理 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 884474398abc9f449e5f6bd82c9f4b981f9a3a43
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261696"
---
# <a name="handling-errors-and-warnings-xmla"></a>エラーおよび警告の処理 (XMLA)
  XML for Analysis (XMLA) の場合は、エラー処理が必要な[Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)または[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドの呼び出しは実行されませんが正常に実行しますが、エラーまたは警告を生成またはが正常に実行、結果が返されますエラーを含みます。  
  
|[エラー]|レポーティング|  
|-----------|---------------|  
|XMLA メソッド呼び出しを実行できない|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エラーの詳細を含む SOAP エラー メッセージを返します。<br /><br /> 詳細については、このセクションを参照してください。 [SOAP エラーの処理](#handling_soap_faults)します。|  
|メソッド呼び出しは成功したが、エラーまたは警告が発生した|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 含まれています、[エラー](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)または[警告](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla)要素のエラーまたは警告は、それぞれ、[メッセージ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)のプロパティ、[ルート](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)要素メソッド呼び出しの結果を格納するとします。<br /><br /> 詳細については、このセクションを参照してください。 [Handling Errors and Warnings](#handling_errors_and_warnings)します。|  
|メソッド呼び出しは成功したが、結果にエラーが含まれる|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インラインを含む**エラー**または**警告**要素のエラーまたは警告を適切な内でそれぞれ[セル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)または[行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla)メソッドの呼び出しの結果の要素。<br /><br /> 詳細については、このセクションを参照してください。[処理インライン エラーおよび警告](#handling_inline_errors_and_warnings)します。|  
  
##  <a name="handling_soap_faults"></a> SOAP エラーの処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、以下の状況が発生した場合に、SOAP エラーを返します。  
  
-   XMLA メソッドを含む SOAP メッセージが、整形式でないか、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって検証できなかった。  
  
-   XMLA メソッドを含む SOAP メッセージに関係する通信エラーまたはその他のエラーが発生した。  
  
-   XMLA メソッドが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで実行できなかった。  
  
 XMLA の SOAP エラー コードは、"XMLForAnalysis" で始まり、その後にピリオドと 16 進数の HRESULT 結果コードが続きます。 たとえば、エラー コード "`0x80000005`" は "`XMLForAnalysis.0x80000005`" という形式になります。 SOAP エラー形式の詳細については、W3C による『Simple Object Access Protocol (SOAP) 1.1』の「Soap Fault」を参照してください。  
  
### <a name="fault-code-information"></a>エラー コード情報  
 次の表は、SOAP 応答の詳細セクションに含まれる XMLA エラー コード情報を示しています。 列は、SOAP エラーの詳細セクションに含まれるエラーの属性です。  
  
|列名|型|説明|Null を許容<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|**ErrorCode**|**UnsignedInt**|メソッドの成功または失敗を示すリターン コード。 16 進数の値に変換する必要があります、 **UnsignedInt**値。|いいえ|  
|**WarningCode**|**UnsignedInt**|警告の状況を示すリターン コード。 16 進数の値に変換する必要があります、 **UnsignedInt**値。|はい|  
|**[説明]**|**String**|エラーを生成したコンポーネントによって返されたエラーまたは警告のテキストと説明。|はい|  
|**Source**|**String**|エラーまたは警告を生成したコンポーネントの名前。|はい|  
|**HelpFile**|**String**|エラーまたは警告について説明しているファイルまたはトピックへのパス、または URL。|はい|  
  
 <sup>1</sup>を示すかどうか、データが必要です返す必要があるまたはかどうか、データが省略可能な列が適用されない場合、null 文字列は許可されています。  
  
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
  
##  <a name="handling_errors_and_warnings"></a> エラーおよび警告の処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 返します、**メッセージ**プロパティ、**ルート**コマンドの実行後に、次の状況が発生する場合、コマンドの要素。  
  
-   メソッド自体は失敗しなかったが、メソッドが成功した後に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスでエラーが発生した。  
  
-   コマンドが成功したときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって警告が返される。  
  
 **メッセージ**プロパティに含まれるその他のすべてのプロパティに依存して、**ルート**要素、1 つまたは複数含めることができます**メッセージ**要素。 各**メッセージ**要素は、1 つを含めることができます**エラー**または**警告**で発生したエラーまたは警告をそれぞれ説明する要素、指定されたコマンド。  
  
 エラーと警告に含まれているの詳細については、**メッセージ**プロパティを参照してください[メッセージ要素&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)します。  
  
### <a name="handling-errors-during-serialization"></a>シリアル化実行時のエラーの処理  
 後にエラーが発生した場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスが正常に実行コマンドの出力をシリアル化を開始した[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を返します、[例外](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla)エラーの時点で別の名前空間内の要素。 その後 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、クライアントに送信する XML ドキュメントが有効なドキュメントになるように、開いている要素をすべて閉じます。 インスタンスを返します、**メッセージ**エラーの説明を含む要素。  
  
##  <a name="handling_inline_errors_and_warnings"></a> インライン エラーおよび警告の処理  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インライン返します**エラー**または**警告**XMLA メソッド自体は失敗しなかったで、メソッドによって返される結果のデータ要素に固有のエラーが発生した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]XMLA メソッドの呼び出しが成功した後のインスタンス。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インラインの提供**エラー**と**警告**問題の特定のセルやその他のデータにある場合は要素内に含まれる、**ルート**要素を使用して、 [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla)セキュリティ エラーやセルの書式設定エラーなど、データ型が発生します。 このような場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を返します、**エラー**または**警告**内の要素、**セル**または**行**エラーを含む要素、または警告、それぞれします。  
  
 次の例から返される行セット内のエラーを含む結果セットを示しています、 **Execute**メソッドを使用して、[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンド。  
  
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
  
## <a name="see-also"></a>関連項目  
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
