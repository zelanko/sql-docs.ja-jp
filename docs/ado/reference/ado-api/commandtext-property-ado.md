---
title: "CommandText プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command15::CommandText
helpviewer_keywords:
- CommandText property [ADO]
ms.assetid: 4dd7e82a-8da5-4a4e-b439-11a29286fa0e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 60ee83c7d1f667feb0b1fcb4985dcd50edfda27b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="commandtext-property-ado"></a>CommandText プロパティ (ADO)
プロバイダーに対して発行できるコマンドのテキストを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**SQL ステートメント、テーブル名、相対 URL、またはストアド プロシージャの呼び出しなど、プロバイダーのコマンドを含む値です。 既定値は空の文字列 ("") です。  
  
## <a name="remarks"></a>解説  
 使用して、 **CommandText**プロパティを設定またはによって表されるコマンドのテキストを返す、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。 通常この SQL ステートメントになりますが、ストアド プロシージャの呼び出しなど、プロバイダーで認識されるコマンド ステートメントの他の種類をすることもできます。 特定の言語仕様またはプロバイダーのクエリ プロセッサによってサポートされているバージョンの SQL ステートメントがあります。  
  
 場合、 [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md)のプロパティ、**コマンド**にオブジェクトが設定されている**True**と**コマンド**オブジェクトを設定すると、開いている接続にバインド**CommandText**プロパティを ADO 準備クエリ (プロバイダーが格納されているクエリのコンパイル形式) を呼び出すと、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)または[を開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドです。  
  
 によって、 [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)プロパティを設定すると、ADO が変わることがあります、 **CommandText**プロパティです。 読み取ることができます、 **CommandText**実際のコマンド テキストを表示するには、いつでもプロパティを ADO は、実行中に使用されます。  
  
 使用して、 **CommandText**プロパティを設定またはファイルやディレクトリなどのリソースを指定する相対 URL を取得します。 リソースは、絶対 URL で、または開いているによって暗黙的に明示的に指定された場所に対する相対[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの使用例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Requery メソッド](../../../ado/reference/ado-api/requery-method.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)

