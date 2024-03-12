# k8sNodeLogViewer
전체적으로, 이 애플리케이션은 Kubernetes의 로그를 보다 쉽게 조회하고 분석할 수 있도록 도와주는 도구입니다. Streamlit을 통해 구성된 사용자 친화적인 인터페이스를 통해 사용자는 웹 브라우저를 통해 Kubernetes 노드의 로그를 간편하게 확인할 수 있습니다.

Streamlit 앱 설정: Streamlit 라이브러리를 사용하여 웹 기반 인터페이스를 구성합니다. st.set_page_config 함수로 앱의 페이지 설정을 정의하고, st.title로 앱의 제목을 지정합니다.

Kubernetes 클러스터 정보 가져오기: get_kube_contexts, get_nodes_for_context, get_logs_for_node 함수를 정의하여 Kubernetes 클러스터의 컨텍스트, 노드, 그리고 특정 노드의 로그를 가져옵니다. 이 함수들은 subprocess.Popen을 사용하여 쉘 명령어를 실행하고 그 결과를 처리합니다.

get_kube_contexts: 사용 가능한 모든 Kubernetes 컨텍스트의 이름을 가져옵니다.
get_nodes_for_context: 주어진 컨텍스트에 속하는 모든 노드의 이름을 가져옵니다.
get_logs_for_node: 특정 컨텍스트와 노드를 대상으로 지정된 라인 수만큼의 로그를 가져옵니다. 여기서 kubectl node-shell 명령을 사용하여 특정 노드의 로그를 조회합니다.
Streamlit 인터페이스 구성: 사용자로부터 입력을 받아 해당 입력에 따라 로그를 조회하고 결과를 표시합니다. st.sidebar.selectbox로 Kubernetes 컨텍스트를 선택하게 하고, st.columns와 st.selectbox, st.number_input을 사용하여 노드 선택과 로그 라인 수 입력을 구성합니다.

로그 조회 및 표시: 사용자가 선택한 컨텍스트, 노드, 그리고 로그 라인 수에 따라 로그를 조회하고, st.text_area를 사용하여 웹 페이지에 로그를 표시합니다.

