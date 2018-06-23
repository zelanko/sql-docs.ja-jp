---
title: '[プロセス チェーンの参照] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6303ea4-fbbf-4cba-bc60-828df62be8c2
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3b3792a55da4ee30d4e3c09a186ca1bf6d32c965
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163898"
---
# <a name="look-up-process-chain"></a>[プロセス チェーンの参照]
  SAP Netweaver BW システムで定義されたプロセス チェーンを参照する場合、 **[プロセス チェーンの参照]** ダイアログ ボックスを使用します。 使用できるプロセス チェーンの一覧が表示されたら目的のチェーンを選択すると、関連するオプションに必要な値が設定されます。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元は、 **[プロセス チェーンの参照]** ダイアログ ボックスを使用します。 SAP BW 変換元の詳細については、「 [SAP BW Source](sap-bw-source.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
 **[プロセス チェーンの参照] ダイアログ ボックスを開くには**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。  
  
3.  **[SAP BW 変換元エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。  
  
4.  **[プロセス チェーン]** で、 **[プロセス チェーンの参照]** ダイアログ ボックスを表示するには、 **[参照]** をクリックします。  
  
     **[プロセス チェーン]** は、 **[実行モード]** の値が **[P - プロセス チェーンをトリガー]** の場合にのみ表示されます。  
  
## <a name="lookup-options"></a>[参照] のオプション  
 参照フィールドで、アスタリスクのワイルドカード文字 (*) を使用して、または部分的な文字列をアスタリスクのワイルドカード文字と組み合わせて使用して、結果をフィルター処理できます。 ただし、参照フィールドを空にした場合、参照操作は、フィールドの空の文字列のみを検索します。  
  
 **Process chain**  
 参照するプロセス チェーンの名前、または部分的な名前をアスタリスクのワイルドカード文字 (*) と入力します。 すべてのプロセス チェーンを含めるには、アスタリスクのワイルドカード文字を単独で使用します。  
  
 **[プロセス チェーンの参照]**  
 SAP Netweaver BW システムで定義されている一致するプロセス チェーンを参照します。  
  
## <a name="lookup-results"></a>参照結果  
 [参照] ボタンをクリックすると、SAP Netweaver BW システムのプロセス チェーンの一覧が、次の列見出しのテーブルに表示されます。  
  
 **[プロセス チェーン]**  
 SAP Netweaver BW システムで定義されたプロセス チェーンの名前を表示します。  
  
 **description**  
 プロセス チェーンの説明を表示します。  
  
 使用できるプロセス チェーンの一覧が表示されたら目的のチェーンを選択すると、関連するオプションに必要な値が設定されます。  
  
## <a name="see-also"></a>参照  
 [SAP bw 変換元エディター&#40;接続マネージャー ページ&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Microsoft Connector 1.1 for SAP BW の F1 ヘルプ](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  