---
title: "CREATE ACTION ステートメント (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE ACTION
- Action
- CREATE
- CREATE_ACTION
dev_langs:
- kbMDX
helpviewer_keywords:
- invocation types [MDX]
- dimensions [Analysis Services], actions
- CREATE ACTION statement
- cubes [Analysis Services], actions
- actions [MDX]
- hierarchies [Analysis Services], actions
ms.assetid: 0419f349-ece2-42ba-8552-a1023f268a41
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 195d9b9d166838a98f9e5c11e10aa9557c8ad0c6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-action"></a>MDX データ定義のアクションを作成します。
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  アクションを作成します。アクションは、キューブ、ディメンション、階層、下位オブジェクトに関連付けることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE ACTION CURRENTCUBE | Cube_Name  
   .Action_Name <action body>  
<action body> ::=   
FOR   
        CUBE   
    | Hierarchy_Name [MEMBERS]   
    | Level_Name [MEMBERS]   
    | CELLS   
    | SET }   
      AS 'MDX_Expression'   
        [, TYPE = '  
              { URL   
            | HTML   
            | STATEMENT   
               | DATASET   
            | ROWSET   
            | COMMANDLINE   
               | PROPRIETARY }   
         ']  
   [ , INVOCATION = 'INTERACTIVE | ON_OPEN | BATCH ' ]  
   [ , APPLICATION = String_Expression ]  
   [ , DESCRIPTION = String_Expression ]  
   [ , CAPTION = 'MDX_Expression' ]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 有効な文字列キューブ名を提供します。  
  
 *Action _ 名前*  
 作成するアクションの名前を指定する有効な文字列です。  
  
 *Hierarchy _ 名前*  
 階層名を指定する有効な文字列です。  
  
 *レベル名*  
 レベル名を指定する有効な文字列です。  
  
 *Member _ 名前*  
 メンバー名またはメンバー キーを指定する有効な文字列です。  
  
 *MDX_Expression*  
 有効な MDX 式です。  
  
 *String_Expression*  
 有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 クライアント アプリケーションが安全でないアクションを作成して実行したり、安全でない関数を使用したりする可能性もあります。 このような状況を避けるためを使用して、 **Safety Options**プロパティです。 詳細については、「Safety Options プロパティ」を参照してください。  
  
> [!NOTE]  
>  このステートメントは、旧バージョンとの互換性のために用意されています。 初めて使用するアクション[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ドリルスルーやレポートの操作などはサポートされていません。  
  
## <a name="action-types"></a>アクションの種類  
 次の表に、さまざまな種類で使用できるアクションの[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
|アクションの種類|Description|  
|-----------------|-----------------|  
|**[URL]**|返されるアクション文字列は、インターネット ブラウザーで開く URL です。<br /><br /> 注: でこの操作が開始されない場合`http://`または`https://`、アクションをブラウザーに使用できる場合を除き、 **SafetyOptions**に設定されている**DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL**です。|  
|**HTML**|返されるアクション文字列は、HTML スクリプトです。 その文字列をファイルに保存して、そのファイルをインターネット ブラウザーで処理します。 この場合は、生成された HTML の一部としてスクリプト全体を実行できます。|  
|**ステートメント**|返されるアクション文字列は、設定によって実行される必要があるステートメント、 **:settext**文字列と呼び出し元にコマンド オブジェクトのメソッド、 **icommand::execute**メソッドです。 コマンドが成功しなかった場合は、エラーが返されます。|  
|**データセット**|返されるアクション文字列は、MDX ステートメントを設定して実行する必要がある、 **:settext**文字列と呼び出し元にコマンド オブジェクトのメソッド、 **icommand::execute**メソッドです。 要求されたインターフェイス ID (IID) 必要があります**IDataset**です。 データセットが作成されれば、コマンドは成功したことになります。 クライアント アプリケーションでは、返されたデータセットをユーザーが表示できるようにする必要があります。|  
|**行セット**|ような**データセット**がの IID を要求するのではなく**IDataset**、クライアント アプリケーションがの IID を要求する必要があります**IRowset**です。 行セットが作成されれば、コマンドは成功したことになります。 クライアント アプリケーションでは、返された行セットをユーザーが表示できるようにする必要があります。|  
|**コマンドライン**|クライアント アプリケーションでアクション文字列を実行します。 その文字列は、コマンド ラインです。|  
|**独自**|クライアント アプリケーションが、特有のアクションに関するカスタム情報や一般的でない情報を認識できるのでない限り、この種のアクションの表示や実行を行うべきではありません。 これらのオプションに適切な制限を設定して、クライアント アプリケーションが明示的に要求する場合を除き、独自のアクションは、クライアント アプリケーションに返されません、 **$application_name**です。|  
  
## <a name="invocation-types"></a>呼び出しの種類  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で使用できる呼び出しの種類は以下のとおりです。 クライアント アプリケーションでは、呼び出しの種類に基づいて、アクションを呼び出すタイミングを判別します。 呼び出しの種類によって、アクションの呼び出しの動作が実際に決まるわけではありません。  
  
|呼び出しの種類|Description|  
|---------------------|-----------------|  
|**対話型**|クライアント アプリケーションは、ユーザーとの対話によってアクションを呼び出します。|  
|**ON_OPEN**|クライアント アプリケーションは、対象のオブジェクトが開かれた時点でアクションを呼び出します。 この呼び出しの種類は、現在実装されていません。|  
|**バッチ**|クライアント アプリケーションは、対象のオブジェクトがバッチ操作にかかわった時点を判別してアクションを呼び出します。 この呼び出しの種類は、現在実装されていません。|  
  
### <a name="scope"></a>スコープ  
 各アクションは、特定のキューブに対して定義するものであり、そのキューブ内で一意の名前を持ちます。 アクションには、以下のいずれかのスコープを設定できます。  
  
 キューブ スコープ  
 特定のディメンション、メンバー、セルに限定されないアクションです。たとえば、"AS/400 実稼働システムの端末エミュレーションの起動" などは、これに相当します。  
  
 ディメンション スコープ  
 特定のディメンションに適用されるアクションです。 この種のアクションは、選択された特定のレベルまたはメンバーに依存しません。  
  
 レベル スコープ  
 特定のディメンション レベルに適用されるアクションです。 この種のアクションは、そのディメンション内で選択された特定のメンバーに依存しません。  
  
 メンバー スコープ  
 特定のレベル メンバーに適用されるアクションです。  
  
 セル スコープ  
 特定のセルだけに適用されるアクションです。  
  
 セット スコープ  
 1 つのセットだけに適用されるアクションです。 名前、 **ActionParameterSet**アクションの式内でアプリケーション用に予約されています。  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント & #40 です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  

