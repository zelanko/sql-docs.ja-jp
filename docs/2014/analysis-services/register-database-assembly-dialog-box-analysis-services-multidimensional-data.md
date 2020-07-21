---
title: '[データベースアセンブリの登録] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidevstudio.assembly.registerassembly.f1
ms.assetid: 0c07cc87-fc94-456f-b878-7b23e39772b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 792b512629df40f67af5a4ffd0f9a3b9787ddb84
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539514"
---
# <a name="register-database-assembly-dialog-box-analysis-services---multidimensional-data"></a>[データベース アセンブリの登録] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [サーバー アセンブリの登録] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのアセンブリ参照のプロパティを設定できます。 **[サーバー アセンブリの登録]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクト エクスプローラー **で** インスタンスまたはデータベースの [アセンブリ] フォルダーを右クリックし、 **[新しいアセンブリ]** を選択します。  
  
## <a name="options"></a>オプション  
  
|期間|定義|  
|----------|----------------|  
|**Type**|アセンブリ参照の種類を選択します。 次の値を指定できます。<br /><br /> **.NET アセンブリ**: <br />                      アセンブリ参照は [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework アセンブリを参照します。<br /><br /> **COM DLL**: <br />                      アセンブリ参照は COM ライブラリを参照します。<br /><br /> <br /><br /> ** \* \* セキュリティ \* \* **に関する注意 COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、[!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)] では、COM アセンブリが非推奨とされました。 COM アセンブリは、今後のリリースではサポートされない可能性があります。|  
|**[ファイル名]**|.NET アセンブリまたは COM ライブラリの完全なパスとファイル名を入力します。|  
|**...**|クリックすると **[ファイルを開く]** ダイアログ ボックスが表示され、.NET アセンブリまたは COM ライブラリの完全なパスとファイル名を選択できます。|  
|**[アセンブリ名]**|アセンブリ参照の名前を入力して設定します。<br /><br /> 注: この値を変更しても、アセンブリ参照が参照するアセンブリの名前は変更されませんが、アセンブリ参照を参照する際に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスまたはデータベースが使用する名前が変更されます。|  
|**[デバッグ情報を含める]**|このオプションを選択すると、.NET アセンブリまたは COM ライブラリのデバッグ情報 (存在する場合) が含まれます。|  
|**[タイムスタンプの作成]**|アセンブリ参照が作成された日時を表示します。|  
|**[スキーマの最終更新]**|アセンブリ参照のメタデータが最後に更新された日時を表示します。|  
|**ソース**|アセンブリ参照のソースを表示します。 このプロパティは通常、アセンブリ参照が参照するアセンブリの完全なパスおよびファイル名を含んでいます。|  
|**セーフ**|この権限セットをアセンブリ参照に使用する場合に、このオプションを選択します。 内部演算とローカル データのアクセスのみがアセンブリに許可されます。 このオプションを設定したアセンブリで実行されるコードでは、ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスできません。<br /><br /> ** \* \* セキュリティ \* \* **に関する注意このオプションは、の外部のリソースにアクセスせずに計算とデータ管理タスクを実行するアセンブリに推奨されるアクセス許可設定です [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。 このオプションは、最も制限の厳しい権限セットを表します。|  
|**外部アクセス**|この権限セットをアセンブリ参照に使用する場合に、このオプションを選択します。 内部演算とローカル データのアクセスのみがアセンブリに許可されます。 この権限セットを持つアセンブリにより実行されるコードでは、ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスすることができます。<br /><br /> ** \* \* セキュリティ \* \* **に関する注意このオプションは、外部のリソースにアクセスするアセンブリに推奨され [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。 このオプションを使用するアセンブリは、既定でサービス アカウントのセキュリティ資格情報を使用して実行されます。 このアセンブリ内のコードは、呼び出し元の Windows 認証セキュリティコンテキストを明示的に偽装することができ [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。 既定ではサービス アカウントとして実行されるため、このオプションを設定したアセンブリを実行する権限は、サービス アカウントとして実行することが許可されているロールにのみ与えます。 このオプションは、 **[安全]** よりも制限が少なく、 **[無制限]** よりも制限の厳しい権限セットを表します。|  
|**無制限**|この権限セットをアセンブリ参照に使用する場合に、このオプションを選択します。 このオプションを選択した場合、アセンブリは内部および外部のリソースに無制限でアクセスできます。 このオプションを設定したアセンブリ内からコードを実行すると、アンマネージ コードを呼び出すことができます。<br /><br /> ** \* \* セキュリティ \* \* **に関するメモアセンブリに無制限のアクセスが必要な場合を除き、このオプションは推奨されません。 セキュリティの観点から見た場合、このオプションは **[外部アクセス]** と同じです。 しかし、 **[外部アクセス]** オプションを使用するアセンブリでは、信頼性と堅牢性を提供するさまざまな保護が得られます。このオプションを使用するアセンブリでは、このような保護はありません。 このオプションを指定すると、アセンブリのコードからプロセス空間に対して無効な操作を実行できるため、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の堅牢性とスケーラビリティを損なう可能性があります。 このオプションは、最も制限の少ない権限セットを表します。注意して使用する必要があります。|  
|**[特定のユーザー名とパスワードを使用する]**|このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトでは指定したユーザー アカウントのセキュリティ資格情報が使用されます。|  
|**ユーザー名**|選択した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトで使用するユーザー アカウントのドメインと名前を入力します。 ユーザー アカウントのドメインと名前は、次の形式で指定します。<br /><br /> *\<Domain name>* **\\** *\<User account name>*<br /><br /> 注: このオプションは、 **[特定のユーザー名とパスワードを使用する]** がオンになっている場合にのみ有効になります。|  
|**パスワード**|選択した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトで使用するユーザー アカウントのドメインと名前を入力します。|  
|**[サービス アカウントを使用する]**|このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトを管理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サービスに関連付けられているセキュリティ資格情報が使用されます。|  
|**[現在のユーザーの資格情報を使用する]**|このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトでは現在のユーザーのセキュリティ資格情報が使用されます。|  
|**[Default]**|このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の既定のユーザー アカウントが使用されます。 このオプションを選択することは、 **[現在のユーザーの資格情報を使用する]** オプションを選択することと同じです。|  
|**説明**|アセンブリ参照の説明を入力して設定します。|  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [多次元モデルのアセンブリの管理](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
