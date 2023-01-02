# ReactJS로 영화 웹 서비스 만들기

## CH2. THE BASICS OF REACT

### Elemet 생성
React.createElement("태그명", property(id/class, style, eventListener...), innerText)

### React | ReactDOM
React: 어플리케이션이 interactive하도록 만들어주는 라이브러리(엔진과 유사)
React-Dom: 모든 React element들을 HTML body에 두게 해주는 라이브러리 또는 패키지 => ReactDOM.render(element명(담을 것), HTML body(담을 위치))

### EventListener
ex) onMouseEnter: () => console.log("")

### JSX
JavaScript를 확장한 문법으로, 구조가 HTML과 유사해 React element를 편하게 만들 수 있음
작성법대로 작성하면 6번 라인의 형태로 변환함 by Babel(코드 변환해주는 역할)

ex) const Button =  () => {
    <button...> InnerText</button>
} 
const Container = () => {
    <div> 
        <Button/>
        <.../>
    </div>
}
//변수명은 항상 대문자로 작성! 그렇지 않으면 HTML 태그로 인식할 것..
ReactDOM.render(<Container />, root);

## CH3. STATE

### ReactJS의 특징
ReRender하는 것은 오로지 바뀐 요소들 => Interactive

### React.useState(val)
['init_val(초기값)' , 'modifier(값을 바꾸는 함수)']
init_val = val(매개변수)
modifier: 값 update + Re-render
ex) const [counter, modifier] = React.useState(0);

### setState
setState(counter+1) 보다는 setState((current) => current+1)이 더 안전함

### event 접근
매개변수 event 내 nativeEvent

## CH4. PROPS

### PROPS란?
부모 컴포넌트에서 자식 컴포넌트로 보내는 데이터(기본값 적용 가능)

** Custom Component에 onClick={...} 달아 놓으면, 이것은 prop일 뿐 EventListener가 아니다. ex) <Btn text={value} onClick={changeValue}/>
=> 직접 element 안에 달아야 한다

### Memo
부모 컴포넌트의 state가 변경되어 자식 컴포넌트들이 다시 렌더링될 때, 렌더링이 불필요한 컴포넌트에 대해 다시 렌더링되는 것을 막을 수 있음 by React Memo
ex) const MemorizedBtn = React.memo(Btn)
=> 필요한 것만 re-render해서 성능 개선 가능

### PropTypes
props가 어떤 모양, 어떤 타입을 받아야 하는지를 특정할 수 있음
<script src="https://unpkg.com/prop-types@15.7.2/prop-types.js"></script>
ex) Btn.propTypes = {
    text: PropTypes.string.isRequired,
    fontSize: PropTypes.number
}
