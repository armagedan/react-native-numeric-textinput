# react-native-numeric-textinput

A React Native TextInput that formats and displays only numeric inputs, including i18n currency formatting. Using the native `number-pad` keyboard type, this component adds or removes a number from the right side of the total, and gives options for the number of decimal places to use or whether to display locale-appropriate nuber grouping.

## Installation

```
npm install @wwdrew/react-native-numeric-textinput
```

## Supported React Native Versions

There is currently a known issue with keyPress events not firing on numeric-style keyboards.
As a workaround, Android uses the default keyboard until this is fixed.

## Usage

```javascript
const Example = () => {
    const [value, setValue] = useState()

    return (
      <View>
        <NumericInput
          type='decimal'
          decimalPlaces={3}
          value={value}
          onUpdate={(value) => setValue(value)}
        />
        <Text>Decimal Value: {value}</Text>
      </View>
    )
}
```

## Props

The only required prop is the `onUpdate` callback, the rest are optional.

- `onUpdate`: (value) => void (**Required**) - called when the value of the TextInput changes.
- `value`: Number - if not provided, will default to `0`.
- `type`: String - either `decimal` or `currency`. If not provided, will default to `decimal`. If type is `currency`, you'll also need to supply a `currency` prop.
- `decimalPlaces`: Number - the number of decimal places to display. Only valid for `decimal` type.
- `currency`: String - the ISO 4217 currency code of the currency to display. Defaults to `GBP`.
- `locale`: String - a BCP 78 language tag specifying the locale used for number formatting. Defaults to `en-GB`.
- `useGrouping`: Boolean - whether to use grouping separators. Defaults to `true`.

## Examples

### Currency

```javascript
    <NumericInput
        type='currency'
        locale='ja-JP'
        currency='JPY'
        value={value}
        onUpdate={(value) => setValue(value)}
    />
```

### Decimal

```javascript
    <NumericInput
        type='decimal'
        decimalPlaces={1}
        useGrouping={false}
        value={value}
        onUpdate={(value) => setValue(value)}
    />
```

# License

MIT
