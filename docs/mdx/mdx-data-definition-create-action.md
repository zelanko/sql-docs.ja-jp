---
title: CREATE ACTION ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1e55a35144fce7b90cf4bb33cbbb82f26d8db62c
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703090"
---
# <a name="mdx-data-definition---create-action"></a>MDX データ操作 - CREATE ACTION


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
  
## <a name="remarks"></a>コメント  
 クライアント アプリケーションが安全でないアクションを作成して実行したり、安全でない関数を使用したりする可能性もあります。 このような状況を避けるためには、使用、 **Safety Options**プロパティ。 詳細については、「Safety Options プロパティ」を参照してください。  
  
> [!NOTE]  
>  このステートメントは、旧バージョンとの互換性のために用意されています。 新しく[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ドリルスルーやレポートの操作などはサポートされていません。  
  
## <a name="action-types"></a>アクションの種類  
 次の表に、さまざまな種類で使用できるアクションの[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]します。  
  
|アクションの種類|説明|  
|-----------------|-----------------|  
|**URL**|返されるアクション文字列は、インターネット ブラウザーで開く URL です。<br /><br /> 注: この操作は値で始まらない場合`https://`または`https://`、アクションは、ブラウザーを使用できませんしない限り、 **SafetyOptions**に設定されている**DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL**.|  
|**HTML**|返されるアクション文字列は、HTML スクリプトです。 その文字列をファイルに保存して、そのファイルをインターネット ブラウザーで処理します。 この場合は、生成された HTML の一部としてスクリプト全体を実行できます。|  
|**ステートメント**|返されるアクション文字列は、設定によって実行される必要があるステートメント、 **:settext**文字列と呼び出し元にコマンド オブジェクトのメソッド、 **icommand::execute**メソッド。 コマンドが成功しなかった場合は、エラーが返されます。|  
|**データセット**|返されるアクション文字列は、MDX ステートメントを設定して実行する必要がある、 **:settext**文字列と呼び出し元にコマンド オブジェクトのメソッド、 **icommand::execute**メソッド。 要求されたインターフェイス ID (IID) にする必要があります**IDataset**します。 データセットが作成されれば、コマンドは成功したことになります。 クライアント アプリケーションでは、返されたデータセットをユーザーが表示できるようにする必要があります。|  
|**行セット**|ような**データセット**がの IID を要求する代わりに**IDataset**、クライアント アプリケーションの IID を要求する必要があります**IRowset**します。 行セットが作成されれば、コマンドは成功したことになります。 クライアント アプリケーションでは、返された行セットをユーザーが表示できるようにする必要があります。|  
|**コマンドライン**|クライアント アプリケーションでアクション文字列を実行します。 その文字列は、コマンド ラインです。|  
|**独自**|クライアント アプリケーションが、特有のアクションに関するカスタム情報や一般的でない情報を認識できるのでない限り、この種のアクションの表示や実行を行うべきではありません。 これらのオプションに適切な制限を設定して、クライアント アプリケーションが明示的に要求する場合を除き、独自のアクションは、クライアント アプリケーションに返されません、 **APPLICATION_NAME**します。|  
  
## <a name="invocation-types"></a>呼び出しの種類  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で使用できる呼び出しの種類は以下のとおりです。 クライアント アプリケーションでは、呼び出しの種類に基づいて、アクションを呼び出すタイミングを判別します。 呼び出しの種類によって、アクションの呼び出しの動作が実際に決まるわけではありません。  
  
|呼び出しの種類|説明|  
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
 1 つのセットだけに適用されるアクションです。 名前、 **ActionParameterSet**は、アクションの式の中のアプリケーションで使用するために予約されています。  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
