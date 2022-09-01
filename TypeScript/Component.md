### Component

컴포넌트에서 form 같이 input 이나 button 같은것들을 한번 정리 FromContainer 라는 방식으로 정리해서 사용할수있음을 배웠다

```ts
import styled from "styled-components";

const Form = styled.form``;

const Label = styled.label``;

const TextArea = styled.textarea``;

const Input = styled.input``;

const Button = styled.button``;

interface IForm extends React.FormHTMLAttributes<HTMLFormElement> {}

interface ILabel extends React.LabelHTMLAttributes<HTMLLabelElement> {}

interface IInput extends React.InputHTMLAttributes<HTMLInputElement> {}

interface ITextarea extends React.TextareaHTMLAttributes<HTMLTextAreaElement> {}

interface IButton extends React.ButtonHTMLAttributes<HTMLButtonElement> {}

const FormContainer = ({ ...props }: IForm) => {
  return <Form {...props}>{props.children}</Form>;
};
FormContainer.Label = ({ ...props }: ILabel) => {
  return <Label {...props}>{props.children}</Label>;
};

FormContainer.TextArea = ({ ...props }: ITextarea) => {
  return <TextArea {...props}>{props.children}</TextArea>;
};

FormContainer.Input = ({ ...props }: IInput) => {
  return <Input {...props}>{props.children}</Input>;
};

FormContainer.Button = ({ ...props }: IButton) => {
  return <Button {...props}>{props.children}</Button>;
};

export default FormContainer;
```

사용 예제는 스타일 컴포넌트로 작성되었음으로 스타일 컴포넌트로 쓰면

const FromInput = styled(FormContainer.Input)
같은 방식으로 사용했다. 더 유려 한 방법도있는것 같으나 일단 내가 이해한대로는 이렇게 사용했다.

사실 알았다 뿐이지 생각은 해봤는데 타입을 주는거 외에 어떤 효용이 있는지 는 잘모르겠다. 타입도 {}랑 props / childeren으로 되어있어서 기본 type 디자인 하려고 쓰는건가 하고 생각은하는데 잘모르겠음
