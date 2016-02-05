{:new_window: target="_blank"} 

# {{site.data.keyword.blockstorageshort}} (BETA) 入門

{{site.data.keyword.blockstoragefull}} では、永続性ストレージを必要とするトランザクション集約型のワークロードやランタイムのために、ブロック・レベルのストレージにアクセスできます。

IBM {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.Bluemix_notm}} を使用して、仮想マシンに接続可能な {{site.data.keyword.blockstorageshort}} ボリュームを作成できます。ブロック・ストレージ・ボリュームに格納されたデータは、お使いの仮想マシンのライフサイクルが過ぎても存続します。IBM {{site.data.keyword.blockstorageshort}} では、OpenStack Cinder を使用してボリュームのライフサイクルを管理します。

{{site.data.keyword.blockstorageshort}} ボリュームは、IBM {{site.data.keyword.blockstorageshort}} サービス・インスタンスを使用して作成します。このボリュームは、特定のデバイスの下で仮想マシンに接続できます。そのデバイスはユーザーが指定しますが、使用可能なデバイス名をシステムが自動的に選択することもできます。仮想マシンは入出力操作を、{{site.data.keyword.blockstorageshort}} サービスとは無関係に、指定のデバイスを使用して直接実行します。

ボリュームのスナップショットをブロック・レベルで作成することもできます。{{site.data.keyword.blockstorageshort}} サービスでは、ボリュームが接続中の場合は、そのボリュームのスナップショットを作成することは許可されません。したがって、作成されたスナップショットはクラッシュ対応になります。 

## {{site.data.keyword.blockstorageshort}} サービスのインスタンス作成方法
お使いのスペースで {{site.data.keyword.blockstorageshort}} サービスのインスタンスを作成するには、以下のステップに従います。
 
1.	{{site.data.keyword.Bluemix_notm}} の**「カタログ」**タブに移動して、検索ボックスに **{{site.data.keyword.blockstorageshort}}** と入力するか、**「サービス」**に移動して**「ストレージ」**を選択します。**{{site.data.keyword.blockstorageshort}}** サービスをクリックします。 
2.	スペース名とサービス名を入力します。プランを選択して、**「作成」**をクリックします。
 	
{{site.data.keyword.blockstorageshort}} サービスは、アンバインドされたコンテキストでのみサポートされます。 

ご使用のスペースに {{site.data.keyword.blockstorageshort}} サービスのインスタンスが作成されます。サービス・インスタンスのアイコンをクリックすれば、いつでも {{site.data.keyword.blockstorageshort}} UI を開いてボリュームを管理できます。

## {{site.data.keyword.blockstorageshort}} ユーザー・インターフェース (UI)
{{site.data.keyword.blockstorageshort}} のグラフィカル・ユーザー・インターフェースでは、ウィンドウ上部に、ストレージ・ボリューム、スナップショット、およびボリュームとスナップショット双方の総ストレージ消費量の概要が表示されます。 

ヘッダーには、最後に UI が最新表示にされた日時が含まれています。必要なら「最新表示」アイコン (円と矢印のアイコン) をクリックして、UI を手動で最新表示にすることができます。 

入力したストリングに基づいてボリュームを探すには検索バーを使用します。入力すると、それにつれて表がフィルタリングされていき、入力した検索ストリングに一致するボリュームのみが表示されます。

概要の下には、ボリューム用とスナップショット用の 2 つのタブがあります。デフォルトでは、ボリュームのタブが選択されています。このタブに載っている表には、使用可能なボリュームと接続済みのボリュームに関する詳細な情報がリストされています。表内のそれぞれの行には、ボリュームの最も重要なプロパティーが表示されます。行を広げれば、より多くのプロパティーが表示されます。接続済みのボリュームには、そのボリュームの接続先の仮想マシンのインスタンスとデバイスも表示されます。 

スナップショットのタブには、類似のプロパティーと動作を持つスナップショットの表が表示されます。 

新規ボリュームを作成したり、既存ボリュームを操作したりするには、表の上にある「作成」アイコンを使用します。スナップショットからボリュームを作成する場合は、「アクション」ドロップダウン・リストを使用することもできます。


## ボリュームのアクション

### ボリュームの作成

1.	**「作成」**をクリックして、**「ボリュームの作成 (Create Volume)」** ダイアログを開始します。
2.	必要なボリュームのサイズを指定します。小数は使用できません。サイズの上限は、組織に割り当てられている割り当て量によって決まります。
3.	名前を指定します。この名前は表示目的でのみ使用されます。
4.	オプションで、ボリュームについてさらに詳しく説明します。 
5.	**「作成」**をクリックして情報を送信し、ダイアログを閉じます。 

ボリュームの作成には、しばらく時間がかかる可能性があります。 

### ボリュームの削除

1.	削除したいボリュームを選択します。
2.	**「削除」**をクリックします。
3.	そのボリュームが削除されたことを確認します。

仮想マシンに接続されているボリュームは削除できません。最初にそのボリュームを切り離す必要があります。

### ボリュームの拡張
**「拡張 (Extend)」**アクションを使用してボリュームのサイズを増やすことができます。ボリュームのサイズを削減することはできません。

1.	拡張するボリュームを選択します。
2.	**「拡張 (Extend)」**をクリックします。
3.	ボリュームの新しいサイズを選択します。ボリュームの新しい合計サイズを指定してください。
4.	**「拡張 (Extend)」**をクリックして情報を送信し、ダイアログを閉じます。 

拡張するには、ボリュームが**使用可能**状態でなければなりません。 

### 仮想マシンに対するボリュームの接続と切り離し
ボリュームは、具体的なデバイス名を持ったデバイスとして、仮想マシンに接続されたり切り離されたりします。仮想マシンがデータをボリューム上で永続的に保持できるようにするには、そのボリュームを仮想マシンに接続する必要があります。

ボリュームを接続するには以下のステップに従います。 

1.	使用可能なボリュームのリストからボリュームを選択します。
2.	**「接続 (Attach)」**をクリックします。
3.	「接続 (Attach)」ダイアログで、ドロップダウン・リストから仮想マシンのインスタンスを選択します。 
4.	オプションで、そのボリュームの接続に使用するデバイスを指定します。デバイスを指定しない場合は、仮想マシンで使用可能なデバイスのうち最初のものがシステムによって自動的に選択されます。
5.	**「接続 (Attach)」**をクリックして情報を送信し、ダイアログを閉じます。

このボリュームは、仮想マシンのインスタンスに関する情報と併せて、接続済みボリュームの表にリストされます。
これで、仮想マシンがデバイスを使ってデータを永続的に保持できるようになりました。 

ボリュームを切り離すには以下のステップに従います。 

1.	接続済みボリュームのリストからボリュームを選択します。 
2.	**「切り離し (Detach)」**をクリックします。
3.	ダイアログで、切り離されたことを確認します。 

ボリュームは、切り離されたら、それ以後仮想マシンのインスタンスで入出力操作に使用することができません。{{site.data.keyword.blockstorageshort}} サービス UI では、そのボリュームは他の仮想マシンに接続できるようになっています。

## スナップショットのアクション

### スナップショットの作成

1.	**「ボリューム」**タブを選択して、ボリュームのリストを取得します。
2.	未接続ボリュームの列で、スナップショットを作成したいボリュームを選択します。選択しているボリュームが未接続であることを確認してください。選択されたボリュームは強調表示されます。 
3.	**「アクション」**をクリックして、ドロップダウン・リストから**「スナップショットの作成 (Create Snapshot)」**を選択します。
4.	スナップショットに名前を付けて、**「作成」**をクリックします。

**注:** ボリュームにスナップショットが存在している間は、そのボリュームを削除することはできません。 

### スナップショットからのボリュームの作成

1.	**「スナップショット (Snapshots)」**タブを選択して、スナップショットのリストを取得します。
2.	ボリュームの作成元になるスナップショットを選択します。選択されたスナップショットが強調表示されます。
3.	**「アクション」**をクリックして、ドロップダウン・リストから**「ボリュームの作成 (Create Volume)」**を選択します。
4.	新規ボリュームに名前を付け、オプションで新しいサイズを指定して、**「作成」**をクリックします。 

**注:** この新規ボリューム・サイズは、スナップショットのサイズ以上でなければなりません。 

### スナップショットの削除

1.	**「スナップショット (Snapshots)」**タブを選択して、スナップショットのリストを取得します。
2.	削除したいスナップショットを選択します。選択されたスナップショットが強調表示されます。
3.	**「アクション」**をクリックして、**「削除」**を選択します。 



># 関連リンク{:class="linklist"}
>## API リファレンス{:id="api"}
>* [OpenStack Block Storage (Cinder) API v2](http://developer.openstack.org/api-ref-blockstorage-v2.html){: new_window}
>
>{:elementKind="article" id="rellinks"}